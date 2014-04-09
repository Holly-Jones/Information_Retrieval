<h1>Architecture of a Search Engine</h1>
<p>An example of an architecture used to
provide a standard for integrating search and related language technology components is UIMA (Unstructured Information Management Architecture).
1
 UIMA
defines interfaces for components in order to simplify the addition of new technologies into systems that handle text and other unstructured data.</p>

<p>An architecture is designed to ensure that a system will satisfy the application
requirements or goals. The two primary goals of a search engine are:</p>

<ul>
<li><strong>Effectiveness (quality): </strong>We want to be able to retrieve the most relevant set of
documents possible for a query.</li>
<li><strong>Efficiency (speed): </strong>We want to process queries from users as quickly as possible.</li></ul>

<p><strong>*The architecture of a search engine is determined by these two requirements.
Because we want an efficient system, search engines employ specialized data structures that are optimized for fast retrieval. Because we want high-quality results,
search engines carefully process text and store text statistics that help improve the
relevance of results.</strong></p>

<h3>The Basic Building Blocks</h3>
<p>Search engine components support two major functions, which we call the indexing process and the query process. The indexing process builds the structures that
enable searching, and the query process uses those structures and a person's query
to produce a ranked list of documents.</p>

<ol>
<li><h2>Indexing</h2></li>

<ul><li><h3>Text Acquisition</h3> The task of the text acquisition component is to identify and make available
the documents that will be searched (i.e. building a collection using a web crawler). In addition to passing documents to the next component in the indexing process, the text acquisition component creates a document data store, which contains the text and metadata for all the documents.
Metadata is information about a document that is not part of the text content,
such the document type (e.g., email or web page), document structure, and other
features, such as document length. </li>
<br>
<li><strong>Document Data Store:</strong> The document contents are typically stored in compressed form for efficiency. The structured data
consists of document metadata and other information extracted from the documents, such as links and anchor text (the text associated with a link). A relational
database system can be used to store the documents and metadata. Some applications, however, use a simpler, more efficient storage system to provide very fast
retrieval times for very large document stores. </li>

<li><h3>Text Transformation</h3> </li>

<li><strong>Parsers:</strong> The parsing component is responsible for processing the sequence of text tokens
in the document to recognize structural elements such as titles, figures, links, and
headings. <strong>Tokenizing</strong> the text is an important first step in this process. Both document and query text must be transformed into tokens in the same manner so that they can be easily compared. <strong>Document structure</strong> is often specified by a markup language such as HTML
or XML. The document parser uses knowledge of the syntax of the
markup language to identify the structure. Both HTML and XML use tags to define document elements. Tags and
other control sequences must be treated appropriately when tokenizing. </li>

<br>

<li><strong>Stopping:</strong> The stopping component has the simple task of removing common words fro m
the stream of tokens that become index terms. The most common words are typically function words that help form sentence structure but contribute little on
their own to the description of the topics covered by the text. Examples are "the",
"of" , "to", and "for" . Because they are so common, removing them can reduce the
size of the indexes considerably.

<br>
<br>
Some stopword lists used in research contain hundreds of words. The
problem with using such lists is that it becomes impossible to search with queries
like "to be or not to be" or "down under". To avoid this, search applications may
use very small stopword lists (perhaps just containing "the") when processing document text, but then use longer lists for the default processing of query text.
</li>

<br>

<li><strong>Stemming:</strong> Stemming is another word-level transformation. The task of the stemming component (or stemmer) is to group words that are derived fro m a common stem.
Grouping "fish", "fishes", and "fishing" is one example. By replacing each member
of a group with one designated word (fo r example, the shortest, which in this case
is "fish"), we increase the likelihood that words used in queries and documents
will match. Stemming, in fact, generally produces small improvements in ranking
effectiveness. However, <strong>aggressive stemming</strong> can cause search problems. It may not be
appropriate, for example, to retrieve documents about different varieties of fish in
response to the query "fishing".  </li>

<br>

<li><strong>Link Extraction and Analysis:</strong> Links and corresponding anchor text are extracted during the document parsing stage, recorded in the document data store, and indexed separately from general text content.<strong> Web search engines make extensive use of this information
through link analysis algorithms such as PageRank (Brin & Page, 1998)</strong>. Link
analysis provides the search engine with a rating of the popularity, and to some
extent, the authority of a page (in other words, how important it is). Anchor text,
which is the clickable text of a web link, can be used to enhance the text content
of a page that the link points to. These two factors can significantly improve the
effectiveness of web search for some types of queries.</li>

<br>

<li><strong>Information Extraction:</strong> Informatio n extraction is used to identify index terms that are more complex than
single words. This may be as simple as words in bold or words in headings, but in
general may require significan t additional computation. Extracting syntactic features such as noun phrases, for example, requires some form of syntactic analysis
or part-of-speech tagging. Research in this area has focuse d on techniques for extracting feature s with specific semantic content, such as named entity recognizers,
which can reliably identify information such as person names, company names,
dates, and locations.</li>

<br>

<li><strong>Classifiers:</strong> The classifier component identifie s class-related metadata for documents or parts
of documents. This covers a range of functions that are ofte n described separately.
Classificatio n techniques assign predefined class labels to documents. These labels
typically represent topical categories such as "sports", "politics", or "business".
<br><br>
Clustering techniques are used to group related documents without predefined
categories. These document groups can be used in a variety of ways during ranking
or user interaction.</li>

<br>

<li><h3>Index Creation</h3></li>

<li><strong>Document Statistics:</strong> The task of the document statistics component is simply to gather and record
statistical information about words, features, and documents. This information
is used by the ranking component to compute scores for documents. The types
of data generally required are the counts of index term occurrences (both words
and more complex features) in individual documents, the positions in the documents where the index terms occurred, the counts of occurrences over groups
of documents (such as all documents labeled "sports" or the entire collection of
documents), and the lengths of documents in terms of the number of tokens. <strong>The document statistics are stored in lookup tables, which are data
structures designed for fast retrieval.</strong></li>

<br>

<li><strong>Weighting:</strong> Index term weights reflec t the relative importance of words in documents, and
are used in computing scores for ranking. <strong>The weighting component calculates weights using
the document statistics and stores them in lookup tables.</strong> Weights could be calculated as part of the query process, and some types of weights require information
about the query, but by doing as much calculation as possible during the indexing
process, the efficiency of the query process will be improved.
<br><br>
<strong>One of the most common types used in older retrieval models is known as tf.idf
weighting. </strong> There are many variations of these weights, but they are all based on a
combination of the frequenc y or count of index term occurrences in a document
(the term frequency, or tf) and the frequenc y of index term occurrence over the
entire collection of documents (inverse document frequency, or idf}. The /^weight
is called inverse document frequency because it gives high weights to terms that
occur in very few documents. A typical formula for idfis log N/n, where N is the total number of documents indexed by the search engine and n is the number of
documents that contain a particular term.</li>

<br>

<li><strong>Inversion:</strong> The inversion component is the core of the indexing process. Its task is to change
the stream of document-term information coming fro m the text transformation
component into term-document information for the creation of inverted indexes.
</li>

<br>

<li><strong>Index Distribution:</strong> The index distribution component distributes indexes across multiple computers
and potentially across multiple sites on a network. Distribution is essential for
efficient performance with web search engines. By distributing the indexes for a
subset of the documents (document distribution], both indexing and query processing can be done inparallel. Distributing the indexes for a subset of terms (term
distribution] can also support parallel processing of queries. Replication is a form
of distribution where copies of indexes or parts of indexes are stored in multiple
site s so that query processing can be made more efficient by reducing communication delays.  </li>




<li><h2>Querying:</h2></li>
<li><strong>Query Input:</strong> The query input component provides an interface and a parser for a query language. The simplest query languages, such as those used in most web search interfaces, have only a small number of <strong>operators</strong>. An operator is a command in the
query language that is used to indicate text that should be treated in a special way. <strong>In the same way that the SQL query language (Elmasri & Navathe, 2006)
is not designed for the typical user of a database application (the end user], these
query languages are not designed for the end users of search applications. </strong></li>

<br>

<li><strong>Query Transformation:</strong> The query transformation component includes a range of techniques that are designed to improve the initial query, both befor e and afte r producing a document
ranking. The simplest processing involves some of the same text transformation
techniques used on document text. Tokenizing, stopping, and stemming must be
done on the query text to produce index terms that are comparable to the document terms.
<br>
<br>
<ol>
<li><strong>Spell Checking</strong> and <strong>Query Suggestion</strong> provide alternatives to the original query. <strong>These techniques often leverage the extensive query logs collected for web applications.</strong></li>
<br>
<li><strong>Query Expansion</strong> and <strong>Relevance Feedback</strong> modify the query by adding additional terms, but usually based on an analysis of term occurrences in documents. <strong>This analysis may use different sources of
information , such as the whole document collection, the retrieved documents, or
documents on the user's computer.</strong> </li>
</ol>

</li>
</ul>
</ol>
