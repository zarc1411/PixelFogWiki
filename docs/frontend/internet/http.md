# HTTP

## Definition

HTTP is basically a protocol that allows the fetching of resources, such as HTML documents. The document can contain texts, images, videos etc. Clients and servers communicate with each in the form of messages. The messages sent by the client is called as the requests and the messages sent back as an answer from the server is called a response.

![Web Document](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview/fetching_a_page.png)

## Proxies

I already know what a client and a server is so I'll skip them. Proxies are like the middlemen between requests and responses. They are used to relay the requests to the server and also for the following things.

1. Caching
2. Filtering (For antivirus or parental controls)
3. Authentication
4. Logging
5. Load Balancing (Using multiple servers to handle different requests)

![Proxies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview/client-server-chain.png)

## Basic aspects of HTTP

1. HTTP is simple (human readable)
2. HTTP is extensible
   So basically you can modify the HTTP readers, which will allow you to add new functionality between a client and a server
3. HTTP is stateless, but not sessionless
   There's no link between two requests on the same connection, this shows that HTTP is stateless. But this can be problematic if two requests need to share the same context/same state. This can be done by HTTP cookies.
4. HTTP and connections
   Connection is controlled at the transport layer. which is totally out of scope of HTTP since HTTP is at the application layer. so HTTP doesn't require the transport protocol to be connection based, but it requires it to reliable. Of the two popular transport protocols TCP and UDP, TCP is reliable and therefore HTTP relies on it for a connection. 

   Before a client and server can exchange a HTTP request response pair,  they need to have a TCP connection. 
   The default behaviour of HTTP/1.0 is to establish a separate connection for every request response pair. Which is inefficient. 
   HTTP/1.1 tried to improve on this by introducing pipelining(which proved to difficult to implement) and persistent connnections.
   HTTP/2 on the other hand allows multiplexing of messages over the same connection, allowing the connection to stay warm and efficient.
   Experiments are going on to find a more reliable transport protocol for HTTP. For example google is experimenting with **QUIC**, which builds on UDP to provide more reliable and secure connection.

## What can be controlled by HTTP

1. Caching
2. Relaxing same origin constraints
3. Proxies and Tunneling
4. Authentication
5. Sessions

## HTTP flow

So basically the HTTP flow is like
1. Open a TCP connection
2. Client sends a message to the server(request)
3. Server sends back a message to the client as an answer(response)

If HTTP pipelining is activated, several requests can be sent without waiting for the first response to be fully received. But this has proven to be difficult to implement.So this was entirely removed in HTTP/2. HTTP/2 on the other hand allows multiplexing of messages on the same connection, this means several messages can be sent and the responses will be received in any order.

## What does multiplexing mean in HTTP2

https://stackoverflow.com/questions/36517829/what-does-multiplexing-mean-in-http-2


## APIs based on HTTP
XMLHttpRequest API
Fetch API
Axios API



