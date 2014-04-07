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
<li><strong>Efficiency (speed): </strong>We want to process queries from users as quickly as possible.</li>

<p><strong>*The architecture of a search engine is determined by these two requirements.
Becaus e we want an efficient system, search engines employ specialized data structures that are optimized for fast retrieval. Because we want high-quality results,
search engines carefully process text and store text statistics that help improve the
relevance of results.</strong></p>
