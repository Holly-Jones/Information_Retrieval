<h1>Crawls and Feeds</h1>

<h3>Retrieving Web Pages</h3>
<p><strong>www.cs.umass.edu/csinfo/people.html</strong></p>

<p>Each web page on the Internet has its own unique uniform resource locator, or
URL. Any URL used to describe a web page has three parts:</p>
<ul>
<li><strong>the scheme (HTTP):</strong> Web pages are stored on web servers,
which use a protocol called Hypertext Transfer Protocol, or HTTP, to exchange
informatio n with client software. Therefore, most URLs used on the Web start
with the scheme http , indicating that the URL represents a resource that can
be retrieved using HTTP. </li>
<br>
<li><strong>the hostname:</strong> The hostname follows, which is the name of the computer that is running the web server that holds this web page. In the figure, the
computer's name is www. cs. umass. edu, which is a computer in the University of
Massachusetts Computer Science department. </li>
<br>
<li><strong>resource name: </strong>This URL refers to a page on that
computer called /csinfo/people.html.</li>

<br>


<strong>Web browsers and web crawlers are two different kinds of web clients, but both
fetch web pages in the same way:</strong>


<ol>
<li>First, the client program connects to a domain
name system (DNS) server. The DNS server translates the hostname into an internet protocol (IP) address.</li>

<br>

<li>The program then attempts to
connect to a server computer with that IP address. Since that server might have
many different programs running on it, with each one listening to the network for
new connections, each program listens on a different port. A port is just a 16-bit
number that identifie s a particular service. By convention, requests for web pages
are sent to port 80 unless specified otherwise in the URL. </li>

<br>

<li>Once the connection is established, the client program sends an HTTP request to the web server to request a page. The most common HTTP request type
is a GET request, for example: </li>

<br>
</ol>
<strong>GET /csinfo/people.html HTTP/1.0 </strong>


<strong>*This simple request asks the server to send the page called /csinfo/people. htm l
back to the client, using version 1.0 of the HTTP protocol specification. </strong>

<br>

<h3>Web Crawlers</h3>
<p>The crawler starts with a set of <strong>seeds</strong>, which are a set of URLs given to it as
parameters. These seeds are added to a URL request queue. The crawler starts
fetching pages from the request queue. Once a page is downloaded, it is parsed
to find link tags that might contain other useful URLs to fetch. If the crawler
finds a new URL that it has not seen before , it is added to the crawler's request
queue, or <strong>frontier</strong>. The frontie r may be a standard queue, or it may be ordered so
that important pages move to the front of the list. This process continues until
the crawler either runs out of disk space to store pages or runs out of useful links
to add to the request queue. </p>

<h3>Threading</h3>
<p>If a crawler used only a single thread, it would not be very efficient. Notice
that the web crawler spends a lot of its time waiting for responses: <strong>it waits for
the DNS server response, then it waits for the connection to the web server to
be acknowledged, and then it waits for the web page data to be sent from the
server. </strong>During this waiting time, the CPU of the web crawler machine is idle and
the network connection is unused. To reduce this inefficiency, web crawlers use
threads and fetch hundreds of pages at once.</p>

<h3>Politeness Policies</h3>
<p>Reasonable web
crawlers do not fetch more than one page at a time from a particular web server.
In addition, web crawlers wait at least a few seconds, and sometimes minutes, between requests to the same web server. This allows web servers to spend the bulk
of their time processing real user requests. To support this, the request queue is
logically split into a single queue per web server. At any one time, most of these
per-server queues are off-limits for crawling, because the crawler has fetched a
page from that server recently. The crawler is fre e to read page requests only from
queues that haven't been accessed within the specified politeness window.</p>

<h3>Freshness</h3>
<p>Web pages are constantly being added, deleted, and modified. To keep an accurate view of the Web, a web crawler must continually revisit pages it has already
crawled to see if they have changed in order to maintain the freshness of the document collection.</p>

<h4>Checking for Freshness</h4>
<p>The HTTP protocol has a special request type called HEAD that makes it easy
to check for page changes. The HEAD request returns only header information
about the page, but not the page itself. Figure 3.5 contains an example HEAD
request and response. The Last-Modified value indicates the last time the page
content was changed. Notice that the date is also sent along with the response, as
well as in response to a GET request. This allows the web crawler to compare the
date it received from a previous GET request with the Last- Modified value from
a HEAD request.</p>

<br>
<strong>Therefore, one of the crawler's jobs is to measure the rate
at which each page changes. Over time, this data can be used to estimate how
frequently each page changes.</strong>

<br>
<h3>Age v.s. Freshness Metrics</h3>
<p>Keeping freshness high seems like exactly what you'd want to do, but optimizing for freshness can have unintended consequences. For example, if you're crawling a page that updates every few minutes then it is best to stop crawling that page completely if you're looking to optimize your <strong>freshness metric</strong>. Obviously, users would not use your search engine if they found popular sites such as cnn.com (which change frequently) to be out of date.</p>

<p>That's why <strong>age is  a better metric to use</strong>. Under the age metric, the page has age 0 until it is changed,
and then its age grows until the page is crawled again. <strong>We can calculated the expected age of a page as well. Studies have shown that, on average, web page updates follow the Poisson distribution, meaning that the time until the next update is governed by an exponential distribution. </strong> </p>

<p><strong>Notice that the second derivative of the Age function is always positive. That
is, the graph is not only increasing, but its rate of increase is always increasing. This
positive second derivative means that the older a page gets, the more it costs you
to not crawl it. Optimizing this metric will never result in the conclusion that
optimizing for freshness does, where sometimes it is economical to not crawl a
page at all.</strong></p>


