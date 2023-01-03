---
title: Status codes
author: jins4731
date: 2023-01-04 01:00:00 +0900
categories: [Error, Backend]
tags: [Error]
pin: true
---

# status code

Web servers communicate the status of a request & response via standardized status codes

## status code : 200

Success !
Request parsed successfully, a response could be generated + sent without any problems

## status code : 404

Client-side error! the requested resource / URL was not found.
Hence te expected response could not be generated.

## status code : 401

client-side error! The requesting client(user) is not authorized to access the requested resource / URL (e.g. because not logged in)

## status code : 500

Server-side error! The request was valid but something went wrong on the server, hence the expected response could not be generated.
