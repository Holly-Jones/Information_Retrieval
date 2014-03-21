CHAPTER 1
What is Information retrieval?
•	Information retrieval is a field concerned with the structure, analysis, organization, storage, searching, and retrieval of information 
-	George Salton (1968)

Primary focus on text documents: web pages, email, scholarly papers, books, and news stories

•	Vertical search – a specialized form of web search where the domain of the search is restricted to a particular topic
•	Enterprise search – involves finding the required information in the huge variety of computer files scattered across a corporate intranet.
•	Desktop search – the personal version of enterprise search, where the information sources are the files stored on an individual computer, including email messages and web pages that have recently been browsed. 
•	Peer-to-peer search – involves finding information in networks of nodes or computers without an centralized control. 

Uses – advertising, intelligence analysis, scientific discovery, health care, customer support, real estate, etc. 

Formal IR Tasks:
•	Filtering: aka tracking involves detecting stories of interest based on a persons interest and providing an alert using email or some other mechanism. 
•	Classification – aka categorization uses a defined set of labels or classes (such as classes listed in Yahoo! Directory) and automatically assigns those labels to documents. 
•	Question Answering – the goal of question answering is to return a specific answer found in the text, rather than a list of documents. 

The Big Issues
One of the biggest issues in IR is document relevance. Simply comparing the text of a query with the text of a document and looking for an exact match, as might be done in a database system or using the grep utility in Unix, produces very poor results in terms of relevance. 

•	Since language can use many different words to express many different things, this sort of algorithmic design will produce a vocabulary mismatch problem.
•	Topical Relevance v.s. User Relevance (just because a document is topically relevant to a query, doesn’t mean it will be considered relevant to the user)

* To address the issue of relevance, researchers propose retrieval models and test how well they work *
•	retrieval models used in IR typically model the statistical features of text rather than the linguistic ones. So, ranking algorithms are far more concerned with word count than they are with whether or not a word is a noun or an adjective. The measure of word frequency is attributed to H.P. Luhn (1950’s) 

Another core issue is evaluation 
•	Evaluation methods assess the quality of results returned on a particular query in order to compare ranking algorithms. 
•	Cyril Cleverdon led the way in developing evaluation methods (1960’s). His two measures included:
o	Recall – the proportion of relevant documents that are retrieved
o	Precision – the proportion of retrieved documents that are relevant

Evaluation of retrieval models and search engines is a very active area, with
much of the current focus on using large volumes of log data from user interactions, such as click through data, which records the documents that were clicked on during a search session. Click through and other log data is strongly correlated with relevance so it can be used to evaluate search, but search engine companies still use relevance judgments in addition to log data to ensure the validity of their results.  

