<html>

<head>
<meta http-equiv="Content-Language" content="zh-tw">
<meta http-equiv="Content-Type" content="text/html">
<meta name="GENERATOR" content="Microsoft FrontPage 5.0">
<meta name="ProgId" content="FrontPage.Editor.Document">
<title>IS392 Assignment 2: Retrieval Experiment</title>
</head>

<body>

<h1 align="center"><font face="Arial">IS392 Assignment 2</font></h1>
<h2 align="center"><b><font face="Arial">Retrieval Experiment</font></b></h2>
<p align="center"><font face="Arial">by Holly Jones</font></p>
<p align="left"><font face="Arial"><b>Credits:</b></font></p>
<ul>
  <li>
    <p align="left"><font face="Arial">The test collection used was <a 
href="http://ir.dcs.gla.ac.uk/resources/test_collections/">LISA</a>.</font></li>  
  <li>  
    <p align="left"><font face="Arial">The experimental IR system was <a href="http://www-2.cs.cmu.edu/~mccallum/bow/">BOW   
toolkit</a>, by <a href="http://www-2.cs.cmu.edu/~mccallum/">Andrew McCallum</a>.</font></li>   
</ul>   
<p><font face="Arial"><b>Query and Relevant Documents:</b></font></p>    
<ul>    
  <li><font face="Arial">The query for my experiment is Query 8:</font></li>     
</ul>     
<blockquote>     
<p><font face="Arial">&quot;<em>I AM INTERESTED IN THE PROFESSIONAL EDUCATION
OF LIBRARIANS, IN PARTICULAR ANY IN SERVICE TRAINING AVAILABLE TO
QUALIFIED LIBRARIANS RATHER THAN EDUCATION AT LIBRARY SCHOOLS.  IN
SERVICE TRAINING COULD BE GENERAL OR IN ONE PARTICULAR AREA OF
LIBRARIANSHIP, E.G. COMPUTERISED RETRIEVAL SYSTEMS. PROFESSIONAL
EDUCATION, IN SERVICE TRAINING, CONTINUING EDUCATION.</em>&quot;</font></p>     
</blockquote>     
<ul>     
  <li><font face="Arial">Relevant documents in the LISA text DB are:</font></li>     
</ul>     
<blockquote>     
<p><font face="Arial">Query 8<br>       
<strong>26 Relevant Refs:</strong><br>       
40, 49, 199, 524, 697, 701, 1043, 1044, 1190, 1191, 1534, 1677, 2039, 2545, 3045, 3716,
4485, 4486, 4499, 4717, 5011, 5170, 5533, 5534, 5723, 5816</font></p>      
</blockquote>      
<p><font face="Arial"><b>Part I: Results</b></font></p>  
<p><font face="Arial"><b>1. Automatic Indexing:</b></font></p>   
<ol>   
  <li><font face="Arial">Model1: <a href="http://web.njit.edu/~haj3/IS392/model1/vocabulary"> vocabulary    
    file</a>, (default settings: no stemming, stopped words       
    removed)</font></li>      
  <li><font face="Arial">Model2: <a href="http://web.njit.edu/~haj3/IS392/model2/vocabulary"> vocabulary    
    file</a>, stemming<span lang="en-us">, stopped words removed.</span></font></li>  
  <li><font face="Arial">Model3: <a href="http://web.njit.edu/~haj3/IS392/model3/vocabulary"> vocabulary    
    file</a>, <span lang="en-us">no stemming, </span>stopped words included</font></li>    
</ol>    
<p><font face="Arial"><b>2. Retrieval: Please list total number of documents retrieved, the link to top 50 documents     
for each model, and which of top 50 documents match the relevant references 
(please give their document numbers, unless none of the 
top 50 matches.):</b></font></p>     
<ol>     
  <li><font face="Arial">Model1: 4,523 documents retrieved.&nbsp; <a href="http://web.njit.edu/~haj3/IS392/model1/retrieved_docs">Top    
    50 documents</a>; 14 of these documents match the relevant references.</font>
    <br><strong>Matches: 40, 49, 524, 1044, 1191, 1534, 2039, 3045, 3045, 3716, 4499, 5011, 5533, 5534</strong></li><br>

  <li><font face="Arial">Model2</font><font face="Arial">:</font> <font face="Arial">802 documents retrieved.&nbsp; <a href="http://web.njit.edu/~haj3/IS392/model2/retrieved_docs">Top    
    50 documents</a></font><font face="Arial">; none of these documents match the relevant references.</font></li><br>


  <li><font face="Arial">Model3:</font> <font face="Arial">4,523 documents    
    retrieved.&nbsp; <a href="http://web.njit.edu/~haj3/IS392/model3/retrieved_docs">Top    
    50 documents</a></font><font face="Arial">; 14 of these documents match the relevant references.</font><br><strong>Matches: 40, 49, 524, 1044, 1191, 1534, 2039, 3045, 3045, 3716, 4499, 5011, 5533, 5534</strong></li>  
</ol> <br> 
<p><font face="Arial"><b>Part II: Analysis of the 
experimental results</b></font></p>      
   
<p:colorscheme
 colors="#FFFFFF,#000000,#1C1C1C,#333399,#00E4A8,#FFCF01,#FF0000,#3333CC"/>
<div v:shape="_x0000_s3074" class="O" style="mso-margin-left-alt:216">
  
  <font face="Arial">
  <p>In information retrieval, the text processing technique used for queries <em>must</em> match the text processing technique used for document parsing and indexing. If different tokenizing processes are used for queries and documents, many of the indexed terms used for documents will simply <strong>not match</strong> the corresponding terms from queries. The detrimental effects of this index to query disparity has been reflected in our retrieval results. For example, both models 1 and 3 produce the exact same retrieval results. (However, this is not surprising, given that the only difference between the two models is the removal of stopwords from the automatic indexing process - a fairly inconsequential difference aside from effecting computational efficiency since the stopwords occupy more disk space). However, model 2 produces no relevant results within the top 50 returned, at all. In order to improve these results, we can infer that the solution would be to increase the flexibility of the search engine to answer a broader range of queries by indexing the words in their original form (instead of stemmed). Stemming can then be done as a type of query expansion. If computational efficiency were not a concern, then one could include both the full words and their stems in the indexing process, in order to provide the maximum amount of search flexibility. 

  <br><br><strong>Based on this information, I went back and re-indexed the text processed by model 2 and made sure NOT to include stemming in the index settings. After making this change, the retrieval results were much better. Like models 1 and 3, model 2 now returns 4,523 documents and 13 of them match the relevant references provided.<br><br>

  Here is the link to the new results for model 2: <a href="http://web.njit.edu/~haj3/IS392/model2/new_retrieved_docs">Improved results for model 2</a></strong>  

  </p></font>
</div>
   
</body>   
   
</html>
