Download Link: https://assignmentchef.com/product/solved-cs60092-assignment2-ranked-retrieval-for-free-text-queries-ir
<br>



This assignment is on building tf-idf based ranked retrieval system to answer free text queries. It is highly recommended that you use python for this assignment as libraries like nltk will make many things easier (stop word removal and lemmatization). However, if you use any other language, you most probably have to design these modules yourselves which might not perform as good as nltk library in python.

<ul>

 <li><a href="https://drive.google.com/file/d/1fXIbuTw8DlARKhGn7k2MkWmkd-DOj7hS/view?usp=sharing">Find your dataset and other required informations.</a>

  <ul>

   <li>Dataset: The dataset contains 1000 text files of the same dataset you used for last assignment.</li>

   <li>Static Quality Score: A python list, containing static quality score of 1000 documents (To know more, please follow chapter 7.1.4 of the textbook by Manning) dictionary where key is document and value is its g(d) value.</li>

   <li>Leaders: A python list, containing index of 30 leader documents. (To know more, please follow chapter 7.1.6 of the textbook by Manning)</li>

  </ul></li>

 <li>Remove stop words, punctuation marks, make everything to lowercase and perform lemmatization to generate tokens from the document (use nltk library in python).</li>

 <li>Tasks

  <ul>

   <li>Let tf idft,d = tft,d ×idft where tfd,t = log10(1 +tf˜ d,t) and idft = log<sub>10</sub>(N/df<sub>t</sub>), <sup>tf</sup>˜ <sub>d,t </sub>denotes number of times term t appears in document d.</li>

   <li>Build InvertedPositionalIndex, that is, a python dictionary with (t,idf<sub>t</sub>) as keys and (d, tf<sub>t,d</sub>) as postings (consider t as term and d as document).</li>

   <li>Build ChampionListLocal, that is, a python dictionary that contains a list for each term, containing the index of top 50 documents with highest tf<sub>t,d </sub></li>

   <li>Build ChampionListGlobal, that is, a python dictionary that contains a list for each term, containing the index of top 50 documents with highest g(d)+tf idf<sub>t,d </sub></li>

  </ul></li>

 <li>Answering free text query: The queries to be answered are free text queries. Remove stop words, punctuation marks, make all lowercase and then apply lemmatization on the query text. Let the resulting query after the first step be Q. Now find the top-10 relevant documents according to each of the following scoring schemes.

  <ul>

   <li>tf idf score(Q, d) = <sub>(</sub><sup>d</sup><sub>d</sub><sup>)</sup><sub>)|</sub>, while V(Q)(t) = idf<sub>t </sub>if t ∈ Q, 0 otherwise, V(d)(t) = tf idf<sub>t,d</sub>,|x| denotes euclidean norm.</li>

   <li>Local Champion List Score(Q, d) = <sub>(</sub><sup>d</sup><sub>d</sub><sup>)</sup><sub>)|</sub>, while V(Q)(t) = idf<sub>t </sub>if t ∈ Q, 0 otherwise, V(d)(t) = tf idf<sub>t,d</sub>, |x| denotes euclidean norm and we will be scoring only documents in A = {d|d ∈ LocalChampionList(t), t ∈ Q}</li>

   <li>Global Champion List Score(Q, d) = <sub>(</sub><sup>d</sup><sub>d</sub><sup>)</sup><sub>)|</sub>, while V(Q)(t) = idf<sub>t </sub>if t ∈ Q, 0 otherwise, V(d)(t) = tf idf<sub>t,d</sub>, |x| denotes euclidean norm. and we will be scoring only documents in A = {d|d ∈ GlobalChampionList(t), t ∈ Q}</li>

   <li>Cluster Prunning Scheme (To know more, please follow chapter 7.1.6 of the textbook by Manning):

    <ul>

     <li>Index of Leaders contains list of leader file names.</li>

     <li>Let your query be Q. Let us define L(Q) = d if tf idf score(d, Q) = maxd∈IndexOfLeaderstf idf score(d, Q)</li>

     <li>Find Followers(L) = {d|tf idf score(d, L) &gt; tf idf score(d, L¯), L¯ ∈</li>

    </ul></li>

  </ul></li>

</ul>

IndexOfLeaders

<ul>

 <li>Cluster Prunning Score(Q, d) = <sub>(</sub><sup>d</sup><sub>d</sub><sup>)</sup><sub>)|</sub>, while V(Q)(t) = idf<sub>t </sub>if t ∈ Q, 0 otherwise, V(d)(t) = tf idf<sub>t,d</sub>, |x| denotes euclidean norm and we will be scoring only documents in A =</li>

</ul>

{d|d ∈ L(Q)∪Followers(L)}

<ul>

 <li>Instruction for submission

  <ul>

   <li>Assume the dataset to be in the path “../Dataset”, i.e., the dataset folder is just outside your python code folder.</li>

   <li>Naming the code file: The name of the code file should be in uppercase letters as below.</li>

  </ul></li>

</ul>

ASSIGNMENT2  &lt; ROLLNO &gt; .py

e.g. :- For a student with roll no 17CS92R02, the code file name should be

“ASSIGNMENT2 17CS92R02.py”.

<ul>

 <li>Reading the queries: Write code which can take “query.txt” file as an argument as below.</li>

</ul>

&gt;&gt; python code.py query.txt

(query.txt file will contain many queries in free text format. For example– religion4

good or bad

There will be one query in each line. This file will remain unknown to you. Your program will be evaluated based on the results it produces for the queries in the above file.)

<ul>

 <li>Saving the search results: Your program should read the queries one by one and get the search results. At the end it should create a text file where you will accumulate your finding in following format.</li>

</ul>

Query result for scoring scheme 1

..

result for scoring scheme N

Next query

…

For example

religion4

&lt; doc1, score &gt;, &lt; doc2, score &gt;, ..

&lt; doc1, score &gt;, &lt; doc2, score &gt;, ..

&lt; doc1, score &gt;, &lt; doc2, score &gt;, .. &lt; doc1, score &gt;, &lt; doc2, score &gt;, ..

good or bad

&lt; doc1, score &gt;, &lt; doc2, score &gt;, ..

&lt; doc1, score &gt;, &lt; doc2, score &gt;, ..

&lt; doc1, score &gt;, &lt; doc2, score &gt;, ..

&lt; doc1, score &gt;, &lt; doc2, score &gt;, ..

The name of the results file should follow the below convention.

RESULTS2  &lt; ROLLNO &gt; .txt

e.g. :- “RESULTS2 17CS92R02.txt”

Please upload a single code with proper naming convention.

<ul>

 <li>Python library restrictions: You can use python libraries like nltk, numpy, os, sys, collections, etc. However, you can’t use libraries like lucene, elasticsearch, or any other search api. If your code is found to use any of such libraries, you will be awarded with zero marks for this assignment without any evaluation.</li>

 <li>Plagiarism Rules: If your code matches (more than 50%) with another student’s code, all those students whose codes match will be awarded with zero marks without any evaluation. Therefore, it is your responsibility to ensure you neither copy anyone’s code nor anyone is able to copy your code.</li>

 <li>Code error: If your code doesn’t run or gives error while running, you will be awarded with zero mark.</li>

</ul>