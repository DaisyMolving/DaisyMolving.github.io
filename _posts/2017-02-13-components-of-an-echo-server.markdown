---
layout: post
comments: true
title: "Components of an Echo Server"
date: 2017-02-13 10:30:30 +0000
---

I am writing an application called an Echo Server, a program in which a client sents a request to a server and receives a copy back (an echo). This application relies on several components to make it work, some of which I will explain below. First though, let's look at a general overview of what an echo server might look like, in order that we might be able to see some of these components in action.

<strong>An Echo Server Diagram</strong>

<p align="center">
<img src="../../../../../../../assets/echo_server_diagram.png">
</p>

An Echo Server is a client/server application. The client sends requests to a server, and the server sends back a response. The request/response in this case is sent with TCP, Transmission Control Protocol. The client sends a request from its own port to a server port. 

The server is constantly listening for a request on its port. If it finds one and accepts it the server creates a socket. A socket is an endpoint on a connection. It sends back a response to the client socket. The client and the server now have an established connection from socket to socket via TCP. The server continues listening on its port for further requests.

<strong>What is the client?</strong>

A client is the part of the program that sends a request to the server. The client side in an Echo Server might ask for a user input. The user types "Hello" and presses enter. Now the client might send a request to the server along with this user input.

<strong>What is the server?</strong>

The server is the part of the program that sends a response to the client request. In an Echo Server this would mean returning the message that was sent to it by the client, providing the connection is accepted.

<strong>What is TCP?</strong>

TCP stands for Transmission Control Protocol. It is a way of sending information over a network. Transmission Control Protocol was designed to be error-checked and reliable. It breaks up the information into streams and checks that the streams are delivered in the correct order. TCP uses a sequence number to identify each byte of data to ensure this. Because it does all of this error checking this does mean that TCP can be a little slower in some cases. For instance if you were speaking to someone on a video call online, or live streaming, checking that all bytes of data were present and correct would take to long to allow a good quality of call. It would lag a lot. For this type of information to be send back and forth a different type of protocol, called User Datagram Protocol (UDP) is often used. 

<strong>What is a port?</strong>

A port is an endpoint of communication in a network, identified with a 16-bit number. There are many well-known ports used for different purposes. For instance Simple Mail Transfer Protocol (SMTP) for email uses port 25, HyperText Transfer Protocol (HTTP) for the web uses port 80 and HTTPS for secure websites uses port number 443. The server listens to the port in order to establish a connection. When computers were only able to execute one program at a time ports were not needed. However now a computer can run several programs all needing to establish connections to servers and so there became a need to specify different ports with different identification numbers.

<strong>What is the Listening Loop?</strong>

The listening loop is when the server "listens" to the port in an infinite loop to check for a request from the client. This is so that if a request is accepted a socket is created to deal with the request and a connection will be established. The port will still be listened to after a connection has been created, and the loop will only be broken with manual shutdown (like when ctrl C or quit is used in a REPL).

<strong>What is a socket?</strong>

A socket is a connection endpoint that is bound to the port. The request gets sent to a Server Socket, and the server response is returned to a Socket on the client side when a connection is established.
