

# Table of contents
- [Table of contents](#table-of-contents)
- [Technical Specs](#technical-specs)
- [1. CSV Import feature](#1-csv-import-feature)
  - [Issues](#issues)
  - [Questions](#questions)
  - [Potential solutions](#potential-solutions)
    - [Issue 1: Large file](#issue-1-large-file)
- [2. Crawling](#2-crawling)
  - [Issue](#issue)
  - [Potential solutions](#potential-solutions-1)
- [3. Error when loading list of articles in CMS](#3-error-when-loading-list-of-articles-in-cms)
  - [Issue](#issue-1)
  - [**Potential solutions**](#potential-solutions-2)
    - [Solution 1: Update the endpoint](#solution-1-update-the-endpoint)
    - [Solution 2: New endpoint](#solution-2-new-endpoint)
    - [Solution 3: Lazy loading](#solution-3-lazy-loading)


# Technical Specs

The Help Center platform is composed of 4 main elements:

* CMS: where merchants can create a Help Center, articles, and categories, this is located inside the helpdesk.
* Front-end: where shoppers can visit the Help Center and read articles.
* API: where the data and business logic is handled.
* Object storage: where we store assets (pictures)
Our helpdesks are hosted on 6 clusters all around the world. 

The Help Center front-end and database are in us-central-1.

# 1. CSV Import feature

One of the key features of the Help Center that we identified is that our clients must easily import their existing help center to Gorgias.

To do so, we developed connectors to integrate with our main competitors directly (Zendesk, Intercom, Re:amaze, Helpdocs) but we also needed to have a CSV import feature so that anyone can easily import a set of articles.
Here is the tech spec that was written at the time about this

(Tech spec: Imports V0) [https://s3-us-west-2.amazonaws.com/secure.notion-static.com/e8660fea-4645-4dff-a20c-896951c0e900/Tech_spec_Imports_V0.pdf]

## Issues
We developed this process and launched it. In our pre-prod environment, everything was fine but on production:

1. if the file is bigger than ~ 500 rows, then the process may fail for everyone after 60 seconds.
2. we noticed that the same CSV file would fail (timeout) for some clients and not for others. This was reproducible, some clients would always fail, and some others would always succeed. The issue does not seem to depend on our clients’ existing data.
3. if some articles contain images that are hosted on competitors’ platform, then the link will be broken when our client delete our competitor’s help center


## Questions
* What do you think of the tech spec? Imagine a member of your team presenting this to you before starting a project. Focus on the form rather than the actual content.
  
The tech spec provided appears to be detailed and well-organized. It clearly defines the key feature, its limitations, and the data that will be imported. It also specifies the merging behavior, languages, and the endpoints for the import process. 

Overall, the tech spec provides a clear and comprehensive understanding of the project requirements and the technical details, which is important for the team to move forward with the project.

* Do you see any obvious flaws? Improvements?
  
Maybe add more information about the CSV file format, for example, the delimiter used, encoding, etc ?

* Can you explain the issues we noticed? Please focus on how those issues are caused by the architecture and how we can improve the architecture (maybe suggest a new diagram).


## Potential solutions


### Issue 1: Large file



# 2. Crawling

## Issue

As of today, it’s super easy to crash our system: we rely on Cloudflare to front and protect our servers. However, an attacker can query random URLs that won’t be cached in Cloudflare and will be sent to our origin.
A script like that will crash our servers quickly


```javascript
while true
	api.get('acme.gorgias.help/'+Math.random())
```

## Potential solutions

There are several possible solutions to address this issue:

1. One solution to this issue would be to add `rate limiting` to the API. This would limit the number of requests that can be made to the API from a single IP address within a certain time period. This would prevent a script like the one you described from overwhelming the servers with too many requests.

2. Another solution would be to add a `Web Application Firewall (WAF)` in front of the origin server. This would provide an additional layer of security and can prevent malicious traffic from reaching the origin server. The WAF can be configured to only allow legitimate requests to pass through, while blocking or rate-limiting requests that match known attack patterns.


# 3. Error when loading list of articles in CMS

## Issue

Just after the deployment, we noticed that in some cases, loading the list of articles in our CMS will crash our server. We implemented a quick fix but have yet to implement a long-term solution.

Go to [https://self-serve.gorgias.com/app/settings/help-center/15/articles](https://self-serve.gorgias.com/app/settings/help-center/15/articles) (use above credentials) and inspect how loading is done.

- Can you guess why it crashed?
- What could we change here?

## **Potential solutions**

The page display the list of articles grouped by category. Uncategorized articles are grouped also in a specific category.

The page makes an API call to the following endpoint `/help-center/help-centers/15/categories/0/tree?depth=-1&locale=en-US&order_by=position&order_dir=asc` to retrieve the list of articles categories and display them on the page.

For each category, the page displays the number of articles available in that category. The problem is that the endpoint mentioned above does not return this information.

So for each category, the page makes an API call to the following endpoint 

`/help-center/help-centers/15/categories/{categoryId}/articles?page=1&per_page=1&version_status=latest_draft`

to retrieve only one article that is not even displayed on the page, so as to retrieve in the pagination info the total number of items available in this category

This is not optimal, because the page makes many more API calls than necessary. The problem raised could therefore come from the fact that a lot of calls are made by the page on loading, which can potentially overload the server ?

### Solution 1: Update the endpoint

A potential solution would be to update the endpoint that retrieves the list of categories, so as to return for each category the number of articles available.

Pros: 

- Single API call when loading the page

Cons:

- Other parts of the application or external services using the API can also call this endpoint and do not need this information.
Maybe add a query params in the url indicating if the endpoint should return the number of articles per category?
- This solution may also change the meaning of the endpoint, causing the endpoint name to no longer be correlated with the returned data. This can also lead to having to add dependencies in the part of the API service that returns the categories

### Solution 2: New endpoint

Define a new endpoint returning the categories + the number of articles available

Pros: 

- Single API call when loading the page

Cons:

- This requires creating a new API endpoint
- Duplication of logic compared to the already existing endpoint?

### Solution 3: Lazy loading

Another solution would be to load only the categories currently visible on the page for the user

For example, when the user loads the page, the page will only display the first ten categories and load for each the number of articles available, and as soon as the user scrolls down the page, the following categories will be retrieved from the API

Pros:

- No need to create a new endpoint or to update the existing endpoint

Cons:

- User experience may be diminished as user will have to wait for categories to load when scrolling down the page