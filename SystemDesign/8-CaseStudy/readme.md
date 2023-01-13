

# Table of contents
- [Table of contents](#table-of-contents)
- [Technical Specs](#technical-specs)
- [1. CSV Import feature](#1-csv-import-feature)
  - [Issues](#issues)
  - [Questions](#questions)
  - [Answers and potential solutions](#answers-and-potential-solutions)
- [2. Crawling](#2-crawling)
  - [Issue](#issue)
  - [Potential solutions](#potential-solutions)
- [3. Error when loading list of articles in CMS](#3-error-when-loading-list-of-articles-in-cms)
  - [Issue](#issue-1)
  - [Potential solutions](#potential-solutions-1)


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

- if the file is bigger than ~ 500 rows, then the process may fail for everyone after 60 seconds.
- we noticed that the same CSV file would fail (timeout) for some clients and not for others. This was reproducible, some clients would always fail, and some others would always succeed. The issue does not seem to depend on our clients’ existing data.
- if some articles contain images that are hosted on competitors’ platform, then the link will be broken when our client delete our competitor’s help center


## Questions
* What do you think of the tech spec? Imagine a member of your team presenting this to you before starting a project. Focus on the form rather than the actual content.
* Do you see any obvious flaws? Improvements?
* Can you explain the issues we noticed? Please focus on how those issues are caused by the architecture and how we can improve the architecture (maybe suggest a new diagram).

## Answers and potential solutions

fdqsdqsd

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

1. Implement `rate limiting` on the origin servers: This can be done by setting up a firewall or using a service like Cloudflare's rate limiting feature to limit the number of requests per IP or per user. This will prevent a single attacker from overwhelming the servers with a large number of requests.
2. Add `caching` to the origin servers: By caching certain types of responses on the origin servers, less load will be placed on them, reducing the likelihood of crashing, for example with `redis` or `node-cache`
3. Use a `Content Delivery Network (CDN)`: Using a CDN can help reduce the load on the origin servers by caching content closer to the end-user. Additionally, configure the CDN to block requests coming from a scraper or a bot
4. Use an `API gateway`: An API gateway can help protect the origin servers by providing features such as rate limiting, caching, and authentication.
5. Implement `DDoS protection`: Distributed Denial of Service (DDoS) protection can help prevent a large number of requests from overwhelming the servers.
6. Add a `WAF (Web Application Firewall)` in front of your servers: A WAF can detect and block malicious traffic before it even reaches your servers, protecting them from crashing.

It's worth noting that these solutions are not mutually exclusive and can be combined to provide a more comprehensive defense against attacks on the system.


# 3. Error when loading list of articles in CMS

## Issue

Just after the deployment, we noticed that in some cases, loading the list of articles in our CMS will crash our server. We implemented a quick fix but have yet to implement a long-term solution.

Go to [https://self-serve.gorgias.com/app/settings/help-center/15/articles](https://self-serve.gorgias.com/app/settings/help-center/15/articles) (use above credentials) and inspect how loading is done.

- Can you guess why it crashed?
- What could we change here?

## Potential solutions