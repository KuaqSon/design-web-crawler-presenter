---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: ./bg.jpeg
# apply any windi css classes to the current slide
class: "text-center"
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: true
# some information about the slides, markdown enabled
info: |
  ## Design a web crawler
  Presentation slides for developers by Son Nguyen
# persist drawings in exports and build
drawings:
  persist: false
# use UnoCSS
css: unocss
---

# Design a web crawler

Presentation slides for developers

Made by Son Nguyen

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

---

# What is a Web Crawler?

A web crawler (also known as a spider) is a system for downloading, storing, and analyzing web pages

<br>

Most prominently, they are one of the main components of web search engines that compile a collection of web pages, index it, and allow users to issue index queries and find web pages that match queries.

<br>

A web crawler bot is like someone whose job is to go through all the books in a disorganized library and organize them in such a way that anyone visiting the library can quickly and easily find the information they need. This process starts by collecting a few web pages and then following links to collect new content.

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
A web crawler (also known as a spider) is a system for downloading, storing, and analyzing web pages. They are used for a wide variety of purposes. Most prominently, they are one of the main components of web search engines that compile a collection of web pages, index it, and allow users to issue index queries and find web pages that match queries.

A web crawler bot is like someone whose job is to go through all the books in a disorganized library and organize them in such a way that anyone visiting the library can quickly and easily find the information they need. This process starts by collecting a few web pages and then following links to collect new content.
-->

---

# What is a Web Crawler?

<div>
  <img
    src="/web-crawler-intro.png"
  />
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

div {
  height: 95%;
}

img {
  max-width: auto;
  height: 100%;
}
</style>

<!--
A web crawler (also known as a spider) is a system for downloading, storing, and analyzing web pages. They are used for a wide variety of purposes. Most prominently, they are one of the main components of web search engines that compile a collection of web pages, index it, and allow users to issue index queries and find web pages that match queries.

A web crawler bot is like someone whose job is to go through all the books in a disorganized library and organize them in such a way that anyone visiting the library can quickly and easily find the information they need. This process starts by collecting a few web pages and then following links to collect new content.
-->

---

# Use Cases of Web Crawler

A crawler is used for many purposes:

- 📝 **Search engine indexing** - A crawler collects web pages to generate a local index for search engines. For example, Googlebot is the web crawler behind the Google search engine.
- 📥 **Web archiving** - This is the compilation of web-based information to store data for future use
- ⛏️ **Web mining** - An incredible opportunity for data mining is created by the exponential growth of the web. Web mining allows the internet to discover valuable information
- 🤹 **Web monitoring** - The crawlers help to monitor copyright and trademark violations over the Internet. Digimarc, for instance, uses crawlers to discover pirated activities and reports.

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Requirements of the System

A simple web crawler should have the following functionalities:

- Given a set of URLs, visit the URL and store the web page.Google search engine.
- Now, extract the URLs in these web pages.
- Append the new URLs extracted to the list of URLs to be visited.
- 🔄 **Repeat the process.**

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# System Analysis and characteristics

It is important to take note of the characteristics of a good web crawler. A web crawler service should have the following features:

- ⛹️‍♂️ **Scalability** - There are billions of web pages to be crawled and analyzed. Therefore, web crawling should be extremely efficient using parallelization
- 🤖 **Robustness** - The internet is full of traps such as bad HTML, unresponsive servers, crashes, malicious links, etc. The crawler must be able to handle all these cases
- 🙅‍♂️ **Politeness** - The web crawler should not make too many requests to a website within a short time interval as it may unintentionally lead to DDoS on several websites
- 🧱 **Extensibility** - The system should be adaptable and flexible to any changes that we might encounter in the future, like if we want to crawl images or music files.
- ⚙️ **Manageability and Reconfigurability** - An appropriate interface is needed to monitor the crawl, including the crawler's speed, statistics about hosts and pages, and the sizes of the main data sets.

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# Estimation of Scale and Constraints

We should estimate the scale by taking many assumptions by discussing them with the interviewer.

- Assuming **1 billion** web pages to be crawled every month, we can estimate the average **QPS** to be: QPS (Query per Second) = 1,000,000,000 / 30 days / 24 hours / 3600 seconds ~ **400 pages per second**.
- We can assume that the peak value of queries per second is 2 times the average, i.e., **800 pages per second**.
- Now, assuming that, on average, a web page is 500 Kb in size, we can estimate storage required per month: 1-billion-page 500k = **500 TB storage per month**.
- Also, assuming data are stored for **five years**, 500 TB _ 12 months _ 5 years = **30 PB**.

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# High-Level Design

<div>
  <img
    src="/high-level-design.png"
  />
</div>

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}

div {
  height: 95%;
}

img {
  max-width: auto;
  height: 100%;
}
</style>

<!--
Seed URLs
A web crawler uses seed URLs as a starting point for the crawl process. For example, to crawl all web pages from a university’s website, an intuitive way to select seed URLs is to use the university’s domain name.
To crawl the entire web, we need to be creative in selecting seed URLs. A good seed URL serves as a good starting point that a crawler can utilize to traverse as many links as possible. The general strategy is to divide the entire URL space into smaller ones. The first proposed approach is based on locality as different countries may have different popular websites. Another way is to choose seed URLs based on topics; for example, we can divide URL space into shopping, sports, healthcare, etc. Seed URL selection is an open-ended question. You are not expected to give the perfect answer. Just think out loud.

URL Frontier
Most modern web crawlers split the crawl state into two: to be downloaded and already downloaded. The component that stores URLs to be downloaded is called the URL Frontier. You can refer to this as a First-in-First-out (FIFO) queue. For detailed information about the URL Frontier, refer to the deep dive.

HTML Downloader
The HTML downloader downloads web pages from the internet. Those URLs are provided by the URL Frontier.

DNS Resolver
To download a web page, a URL must be translated into an IP address. The HTML Downloader calls the DNS Resolver to get the corresponding IP address for the URL. For instance, URL www.wikipedia.org is converted to IP address 198.35.26.96 as of 3/5/2019.

Content Parser
After a web page is downloaded, it must be parsed and validated because malformed web pages could provoke problems and waste storage space. Implementing a content parser in a crawl server will slow down the crawling process. Thus, the content parser is a separate component.

Content Seen?
Online research [6] reveals that 29% of the web pages are duplicated contents, which may cause the same content to be stored multiple times. We introduce the “Content Seen?” data structure to eliminate data redundancy and shorten processing time. It helps to detect new content previously stored in the system. To compare two HTML documents, we can compare them character by character. However, this method is slow and time-consuming, especially when billions of web pages are involved. An efficient way to accomplish this task is to compare the hash values of the two web pages [7].

Content Storage
It is a storage system for storing HTML content. The choice of storage system depends on factors such as data type, data size, access frequency, life span, etc. Both disk and memory are used.
• Most of the content is stored on disk because the data set is too big to fit in memory. • Popular content is kept in memory to reduce latency.

URL Extractor
URL Extractor parses and extracts links from HTML pages. Figure 9-3 shows an example of a link extraction process. Relative paths are converted to absolute URLs by adding the “https://en.wikipedia.org” prefix.

URL Filter
The URL filter excludes certain content types, file extensions, error links and URLs in “blacklisted” sites.

URL Seen?
“URL Seen?” is a data structure that keeps track of URLs that are visited before or already in the Frontier. “URL Seen?” helps to avoid adding the same URL multiple times as this can increase server load and cause potential infinite loops.
Bloom filter and hash table are common techniques to implement the “URL Seen?” component. We will not cover the detailed implementation of the bloom filter and hash table here. For more information, refer to the reference materials [4] [8].

URL Storage
URL Storage stores already visited URLs.
So far, we have discussed every system component. Next, we put them together to explain the workflow.
-->

---

# The Workflow of a Web Crawler System

The crawling process consists of several threads, and each thread performs work cycles repeatedly. The following is a brief overview of a work cycle:

1. Add seed URLs to the URL Frontier
2. HTML Downloader fetches a list of URLs from URL Frontier.
3. HTML Downloader gets IP addresses of URLs from DNS resolver and starts downloading.
4. Content Parser parses HTML pages and checks if pages are malformed.
5. After content is parsed and validated, it is passed to the “Content Seen?” component.
6. “Content Seen” component checks if a HTML page is already in the storage.
    - If it is in the storage, this means the same content in a different URL has already been processed. In this case, the HTML page is discarded.
    - If it is not in the storage, the system has not processed the same content before. The content is passed to Link Extractor.


<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---

# The Workflow of a Web Crawler System

The crawling process consists of several threads, and each thread performs work cycles repeatedly. The following is a brief overview of a work cycle:

7. Link extractor extracts links from HTML pages.
8. Extracted links are passed to the URL filter.
9. After links are filtered, they are passed to the “URL Seen?” component.
10. “URL Seen” component checks if a URL is already in the storage, if yes, it is processed before, and nothing needs to be done.
11. If a URL has not been processed before, it is added to the URL Frontier.

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

---
layout: center
class: text-center
---

# Q & A

---

# Reference

[System Design Interview – An insider's guide](https://www.amazon.com/System-Design-Interview-insiders-Second/dp/B08CMF2CQF)
