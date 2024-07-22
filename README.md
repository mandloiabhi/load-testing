# load-testing
Build a load generator and perform a load test on the web server developed.
I also used Valgrind to fix errors before running the load test, to avoid server crashes due to memory errors.
Closed-loop load generator client
To measure the capacity of our web server, we first build a load generator client to fire requests at the server rapidly. This client acts as a closed-loop load generator, i.e., load is generated from a certain number of concurrent emulated users.
The load generator is a closed-loop multi threaded program, with the number of concurrent users/threads, think time between requests, and the duration of the load test specified as command line arguments. Each thread of the load generator will emulate a HTTP user/client, by sending a HTTP request to the server, waiting for a response from the server, and firing the next request after the think time. After all the load generator threads run for the specified duration, the load generator compute (across all its threads) and display the following performance metrics before terminating.

Average throughput of the server, defined as the average number of HTTP requests per second successfully processed by the server for the duration of the load test.

Average response time of the server, defined as the average amount of time taken to get a response from the server for any request, as measured at the load generator.

Perform a load test on our server. Run multiple experiments by varying the load level (i.e., number of concurrent load generating threads) at the load generator. Use  performance graphs (In a file decs_p4_doc.pdf) to estimate the capacity of our server, and identify the resource causing the performance bottleneck.

and the resource causing the problem was the queue that holds the requests.

Steps to Perform Test

1)Prepare executables of  server by running respective makefile in respective directory (simply execute make command).
2) executables of load balancer can be prepared by : gcc load_gen.c -o load_gen -lpthread

3)start the web server by executing server executable with port number as argument

4)generate load on the web server by executing load_generator executable with hostname, server port number, number of concurrent users, think time (in seconds) and test duration (in seconds) as argument

For example:

./server <port number>

followed by

./load_gen <hostname> <server port> <number of concurrent users> <think time (in s)> <test duration (in s)>

for example

./load_gen localhost 8088 40 2 50


