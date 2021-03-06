# web-proxy
A webproxy server which could handle GET, POST, CONNECT

In this project we built an http proxy, a server who is able to parser and forward the requests to the origin server on behalf of the client and also the response from the remote server to the client.
Our proxy can cache responses to avoid re-fetching the new response when there comes identical and valid request. Note that our cache will not be able to conform to the complete cache-policy of http protocol and handle all the cases as the official requirement.

Our proxy shall handle three method, users can configure their browser and browse typical webpages by using our proxy.
We produce a log file in /var/log called erss-proxy.log which kept records of the information of request, response, also the cache and errors, etc.


Our proxy still has some explicit flaws. 

First, there are some test cases that our proxy cannot handle correctly:
1 The tunnel request cannot always be successfully connected;
2 The cache validation/revalidation policy was not strictly implemented; 

Second, the data structure of our cache is a basically a doubly linked list , which will perform search in O(n) time, the performance of it can be improved by modifying the structure into some more efficient way; 

Finally, there are some security issues related to the potential risks and dangers in our program, please see the details in our dangers.txt.


The project includes the following files:
Makefile	cache.h		log.c		parser.h	socket.h
README		clientSocket.c	log.h		serverSocket.c
cache.c		dangers.txt	parser.c	socket.c

Please see our comments in each file for details about the code.


To run the program, please follow the instruction below:
Note: Please run the code under a linux machine environment
1 Open two terminal;
2 In terminal 1: make clean; make (To compile and build the executable files)
3 In terminal 2: gcc -o clientSocket clientSocket.c
4 In terminal 1: ./serverSocket <port>
5 In terminal 2: ./clientSocket <port> <number 1 - 7>(refer to the corresponding command line number)


Reference:
Hypertext Transfer Protocol -- HTTP/1.1(2014) Retrieved from https://www.w3.org/Protocols/rfc2616/rfc2616.html
