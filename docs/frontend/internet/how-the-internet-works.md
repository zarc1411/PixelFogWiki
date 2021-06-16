---
sidebar_position: 6
---

# How the Internet works

## Active Learning
This is a very simplistic view of how the internet works. The idea is that internet is just a wire to which all computers are connected. Your computer is called a client. It's not directly connected to the internet. It's connected to the ISP which is connected to the internet, and this ISP gives back whatever it got from the server which is conncted to the internet to the client. 

A router is connected to the ISP, and clients are connected to it. Information is sent in the form of packets. Your packet is wrapped with your PCs IP, and then it goes through the router and is wrapped with its IP and so on it gets more wrappers. Then when it comes back the wrappers go away.
This is how the router knows whom to send back the data.

[Source](https://youtu.be/7_LPdttKXPc)

## A bit detailed example

There's something called the DNS, which is like a phonebook containing domain names(like google.com) and their respective IP addresses. Whenever your browser makes a request to xyz.com, it will check in the DNS to find out what is the IP address of this particular website. And when it gets that info it makes a request to that website.

And there are protocols that describe how data is passed, some examples are HTTP/HTTPS , TCP etc. These protocols have different purposes.

How does your mobile get data? Well the cell tower sends back the information it got from the datacenter (through the optical fiber cables in pieces) in the form of electro magnetic waves. Electro magnetic waves are formed when an electric field comes in contact with a magnetic field.

[Source](https://youtu.be/x3c1ih2NJEg)

## Deeper Dive

### A simple network

For computers to be connected to each other , they need to be connected either physically or wirelessly. Lets focus on physically. This seems normal if the number of computers is low, like for example just 2, but what if there were 10 computers? There would be so many wires and so many connections. 

![computers](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work/internet-schema-2.png)

This is where the router comes in, it simplifies the number of connections.

![router](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/How_does_the_Internet_work/internet-schema-3.png)

And then these routers are connected to even more routers. This is how we are able to scale infinitely.

