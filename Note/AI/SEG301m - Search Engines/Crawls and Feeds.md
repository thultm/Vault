# 3.1 What to search?
- Everything you possibly can!
- Every document answers at least one question
- The best documents answer many more
# 3.2 Crawling the Web
- Build a search engine that searches web pages $\rightarrow$ need the content of web pages $\rightarrow$ copy web pages 
- Finding and downloading web pages: crawling, the program downloads pages: web crawler
- Challenge:
	- The sheer scale of the Web: at least tens of billions of pages on the Internet and constantly created
	- Web pages are usually not under the control of the people building the search engine database
- Each web page has unique uniform resource locator (URL) ![[Pasted image 20230912153758.png]]
- The most common HTTP request type is `GET` request: ![[Pasted image 20230912153901.png]]
  $\rightarrow$ asks server to send the page called `/csinfo/people.html`
- Other request is POST request: similar to `GET` request but sending additional information to the server $\rightarrow$ click a button to buy something or to edit a web page
- The web crawler connects to web servers to find pages. Pages may link to other pages on the same server or on different servers
# 3.3 Crawling documents and emails
# 3.4 Documents feeds
# 3.5 Conversion problem: character encodings
# 3.6 Storing documents
# 3.7 Delete duplicates
# 3.8 Remove noise
