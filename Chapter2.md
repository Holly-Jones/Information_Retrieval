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
<li><h2>Indexing:</h2></li>

<ul><li><h3>Text Acquisition:</h3> The task of the text acquisition component is to identify and make available
the documents that will be searched (i.e. building a collection using a web crawler). In addition to passing documents to the next component in the indexing process, the text acquisition component creates a document data store, which contains the text and metadata for all the documents.
Metadata is information about a document that is not part of the text content,
such the document type (e.g., email or web page), document structure, and other
features, such as document length. </li>
<br>
<li><strong>Document Data Store:</strong> The document contents are typically stored in compressed form for efficiency. The structured data
consists of document metadata and other information extracted from the documents, such as links and anchor text (the text associated with a link). A relational
database system can be used to store the documents and metadata. Some applications, however, use a simpler, more efficient storage system to provide very fast
retrieval times for very large document stores. </li>

<li><h3>Text Transformation:</h3> </li>

<li><strong>Parsers:</strong> The parsing component is responsible for processing the sequence of text tokens
in the document to recognize structural elements such as titles, figures, links, and
headings. <strong>Tokenizing</strong> the text is an important first step in this process. Both document and query text must be transformed into tokens in the same manner so that they can be easily compared. <strong>Document structure</strong> is often specified by a markup language such as HTML
or XML. The document parser uses knowledge of the syntax of the
markup language to identify the structure. Both HTML and XML use tags to define document elements. Tags and
other control sequences must be treated appropriately when tokenizing. </li>

</ul>
<li><h2>Querying:</h2></li>
</ol>
