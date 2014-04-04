<h1>CH 1: Search Engines & IR</h1>
<p><strong>Information Retrieval</strong> is a field concerned with the structure, analysis, organization, storage, searching, and retrieval of information.</p>

<ul>
<li>The primary focus of the field since the 1950s has been on text and text documents. Web pages, email, scholarly papers, books, and news stories are just a few of the many examples of documents.</li>
<br>
<li>Defining the meaning of a word, a sentence, a paragraph, or a whole news
story is much more difficult than defining an account number, and consequently
comparing text is not easy. Understanding and modeling how people compare
texts, and designing computer algorithms to accurately perform this comparison,
is at the core of information retrieval.</li></ul>

<h4>Types of Search</h4>
<p><em>Although searching the World Wide Web (web search] is by far the most
common application involving information retrieval, search is also a crucial part
of applications in corporations, government, and many other domains.</em></p>

<ul>
<li><strong>Vertical Search:</strong> is a specialized form of web search where the domain of the search is restricted to a particular topic.</li>
<br>
<li><strong>Enterprise Search:</strong> involves finding the required information in the huge variety of computer files scattered across a corporate intranet.</li>
<br>
<li><strong>Desktop Search:</strong> is the personal
version of enterprise search, where the information sources are the files stored
on an individual computer, including email messages and web pages that have recently been browsed.</li>
<br>
<li><strong>Peer-to-Peer Search:</strong> involves finding information in networks
of nodes or computers without any centralized control. This type of search began
as a file sharing tool for music but can be used in any community based on shared
interests, or even shared locality in the case of mobile devices. </li>
<br>
<h4>Information Retrieval Tasks</h4>
<p>Search based on ad hoc user queries is not the only text-based task that is studied in information retrieval. Other important tasks include:</p>
<ol>
<li><strong>Filtering:</strong> Filtering or tracking involves detecting stories of interest
based on a person's interests and providing an alert using email or some other
mechanism.</li>
<br>
<li><strong>Classification:</strong> Classification or categorization uses a defined set of labels or classes (such as the categories listed in the Yahoo! Directory
4
) and automatically assigns
those labels to documents.</li> 
<br>
<li><strong>Question Answering:</strong> Question answering is similar to search but is aimed
at more specific questions, such as "What is the height of Mt. Everest?" . The goal
of question answering is to return a specific answer found in the text, rather than
a list of documents.</li>

<br>
<h3>Big Issues in IR</h3>
<p><strong>Relevance:</strong> There are many factors that contribute to a person's decision as to whether a particular document returned to them is relevant or not. <br><br>
<strong>*Simply comparing the text of a query
with the text of a document and looking for an exact match, as might be done in
a database system or using the grep utility in Unix, produces very poor results in
terms of relevance. One obvious reason for this is that language can be used to express the same concepts in many different ways, often with very different words.
This is referred to as the <em>vocabulary mismatch problem</em> in information retrieval. </strong></p>

<br>

<p><strong>Solution:</strong> To address the issue of relevance, researchers propose <strong>retrieval models</strong> and test
how well they work. A retrieval model is a formal representation of the process of
matching a query and a document. It is the basis of the <strong>ranking algorithm</strong> that is
used in a search engine to produce the ranked list of documents. A good retrieval
model will find documents that are likely to be considered relevant by the person
who submitted the query.</p>

<p><strong>Evaluation:</strong> Another core issue for information retrieval is evaluation. Since the quality of
a document ranking depends on how well it matches a person's expectations, it
was necessary early on to develop <strong>evaluation measures</strong> and experimental procedures for acquiring this data and using it to compare ranking algorithms.</p>

<p>[<strong>Precision = </strong>The proportion of retrieved documents that are relevant]</p>
<p>[<strong>Recall = </strong>The proportion of relevant documents that are retrieved (it's assumed that all relevant documents for a query are known, which is obviously impossible on the web)]</p> 

<h4>*Evaluation Measures NOW*</h4>
<p>Evaluation of retrieval models and search engines is a very active area, with
much of the current focus on using large volumes of log data from user interactions, such as clickthrough data, which records the documents that were clicked
on during a search session. Clickthrough and other log data is strongly correlated
with relevance so it can be used to evaluate search, but search engine companies
still use relevance judgments in addition to log data to ensure the validity of their
results.</p>

<br>
<br>
<h2>Search Engines</h2>
<p>A search engine is the practical application of information retrieval techniques
to large-scale text collections.</p>

<h3>Search Engine Design Considerations</h3>
<h4>Performance</h4>
<ul>
<li><strong>Response Time:</strong> is the delay between submitting a query and receiving the result list.</li>
<li><strong>Query Throughput:</strong> measures the number of queries that can be processed in a given time.</li>
<li><strong>Indexing Speed:</strong> is the rate at which text documents can be transformed into indexes
for searching. (An index is a data structure that improves the speed of search). Another important performance measure is how fast new data can be incorporated into the indexes.</li>
<li><strong>Coverage:</strong> measures how much of the existing information
in, say, a corporate information environment has been indexed and stored in the
search engine.</li>
<li><strong>Recency/Freshness: </strong>measures the "age" of the stored information.</li>
<li><strong>Scalability:</strong> Designs that
work for a given application should continue to work as the amount of data and
the number of users grow.</li>
<li><strong>Adaptability</strong> In order to support the need for scalability, search engines have to be customizable
or adaptable. This means that many differen t aspects of the search engine, such as
the ranking algorithm, the interface, or the indexing strategy, must be able to be
tuned and adapted to the requirements of the application.</li>


