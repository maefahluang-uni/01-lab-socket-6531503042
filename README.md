# Web Lab - Server with Socket
 This lab demonstrate how to create a simple web server that run on a localhost at specified network port. Server utilises Java's thread to keep server running to wait for a request.

 ## How to do lab
 1. study lecture materials.
 2. learn the purpose of statements shown in the slides
 3. start working on the exercise by cloning this project to your VS Code.
 4. answer question in the blank when it ask you to do so
 5. push back the code to Github to submit this lab.
 
**You have to carefully read the instruction. DO NOT skip any part.**

## Exercise A. Complete Server
The `MockWebServer` in package `th.mfu` serves the web server in our system. It get a request and response back `Hello Web!` message. You have to complete its source code by following the steps below and look for hints at `TODO` in the source code. The `MockWebServer` implements `Runnable` to make it be able to run as a thread. You must complete `run` method.
1. Create a server socket using `ServerSocket` in java.net library by openning at specified `port` defined from the constructor. 
2. Within infinite while loop,  accept incoming client connections to obtain client socket.
2. After that, create input and output streams for the client socket with `BufferedReader` and `PrintWriter`
3. Then, read the request from the client and send a response to the client. For example, if the server runs on port 8080, it should print out `Hello, Web! on Port 8080` 
4. Finally, close the client socket 
5. Study the code in `main()` and tell me What it does?
```
Your explanation here.
Answer: In the `main()` method, two threads (`server1` and `server2`) are created, each running an instance of the `MockWebServer` on different ports (8080 and 8081). It then waits for user input to stop the servers. The `try` block handles potential exceptions, including IO exceptions. The servers are stopped using the `stop()` and `interrupt()` methods, and the program is terminated using `System.exit(0)`.

 And there're other method like: if user press anykey in terminal the server will be stopped 
 And there're also have try & catch block that will block any error stuff of code that are in match the try & catch condition like in this code is IOEXception that print e.trace that mean it'll print all of the error, In the statement System.exit(0) at the end of try block is used to terminate the program. This statement is executed regardless of whether or not an exception.
```
6. Run the `main()`, point the web browser to `http://localhost:8080` and `http://localhost:8081`
It should shows a simple HTML with the word such as  `Hello, Web! on Port 8080`.

## Exercise B. Complete Client
The `MockWebClient` is in the same package. This class mocks the web browser by sending a `HTTP GET` request to the web server and receive the message back to print out in the console. The `main()` method contains the source code to do this.
1. Create a socket to port `8080` using `Socket` class
2. create input and output streams for the client socket with `BufferedReader` and `PrintWriter`
3. send out the `HTTP GET` though `PrintWriter`
4. receive the response back from the web server and  print out to console
5. Finally, close the  socket 
6. Make sure the server is running and run this `MockWebClient` to see the result. It should print out message like below: 

```
HTTP/1.1 200 OK
Content-Type: text/html

<html><body>Hello, Web! on Port 8080</body></html>
```

## Exercise C. Unit Testing Mockup Server
Run the `MockWebServerTest` in `src/test/java`. This test script create a new object of MockWebServer on port 8080 and evaluate if the returned message is correct. 

## Challenge
Think about the following,  modify the code to experiment it and put your thought below.
- How can we run `MockWebserver` on different port? 
- How can we run more than 2 instances of  `MockWebserver`? 
- How can we change the content in HTML such as showing table, more text and adding images?
- What would be the benefit of running many instances?

```
  Your thought here...
1. Running the `MockWebServer` on different ports can be achieved by creating instances of the class with different port values passed to the constructor. For example: MockWebServer serverPort8082 = new MockWebServer(8082);
Thread server3 = new Thread(serverPort8082);
server3.start();

2. Running more than two instances of `MockWebServer` can be done similarly by creating additional instances and threads with different port values. For example:
MockWebServer serverPort8083 = new MockWebServer(8083);
Thread server4 = new Thread(serverPort8083);
server4.start();


3. To change the content of the HTML response, you can modify the `response` string in the `run()` method of the `MockWebServer` class. You can add additional HTML tags, text, or images as needed.

4. The benefits of running many instances include improved concurrency, load distribution, resource utilization, scalability, isolation, and the ability to simulate real-world distributed systems. Running multiple instances allows the server to handle multiple client connections concurrently, distribute the load across instances, and provide fault tolerance and redundancy.



```
**Please push the code back to Github to submit this lab**
