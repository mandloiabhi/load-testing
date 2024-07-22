# load-testing
Build a load generator and perform a load test on the web server developed.


1)Prepare executables of load_generator and server by running respective makefile in respective directory (simply execute make command).
2)start the web server by executing server executable with port number as argument
3)generate load on the web server by executing load_generator executable with hostname, server port number, number of concurrent users, think time (in seconds) and test duration (in seconds) as argument
For example:
./server <port number>
followed by
./load_gen <hostname> <server port> <number of concurrent users> <think time (in s)> <test duration (in s)>
for example
./load_gen localhost 8088 40 2 50

