---
sidebar_position: 3
---

# DNS

## What is DNS
Simply put, the DNS is the phonebook of the internet. Each website has its own unique address. Browsers make requests to these websites to their unique IP address. But its hard for a human to remember IP addresses. That's why every website has a domain. Humans can easily remember domains like (www.example.com). THe job of the DNS is to convert these human readable domains to their unique IP addresses, so that browsers can make requests to them. As simple as that.


## DNS servers

1. **DNS recursor** - The recursor can be thought of as a librarian who is asked to go find a particular book somewhere.
2. **Root nameserver** - This is the first step when its come to finding the unique IP addresses of those domain names. It can be thought of as an index in the library that points to different racks of books.
3. **Top Level Domain server** - This server will try to find a specfic rack of books. In the case of website address it would be the *.com* of the address *www.example.com*
4. **Authoritative nameserver** - This will find the specifc book in the rack of books.

[Source](https://www.cloudflare.com/en-in/learning/dns/what-is-dns/)
