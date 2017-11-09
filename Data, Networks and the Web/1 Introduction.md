# Introduction

---

# What is a web application?
> "A client-server software application in which the user interface runs in a web browser" (Wikipedia)  

> "A computer program which allows a user to submit and retrieve data to/from a database over the internet using their preferred browser" (www.acunetix.com)  

> "An application in which all or some parts of the software are downloaded from the Web each time it is run. It may refer to browser-based, 'rich client' and mobile web apps" (PC Magazine)  

# Thinking Points:
- Is there a difference between a website and a web application?
- Can a web application exist without the internet?
- What does it mean to say an application is 'data-driven'?
- Where is the data in a 'data-driven' web application?

# Data-Driven Applications
- Act on data!
- Compelled by **collection**, **presentation** and **analysis** of data
- **As opposed to** *Purely* user experience (but that's not to say a data-driven app can't deliver an exceptional user experience too)

# Life and times of a web request
1. URL is typed in the browser
2. Check browser cache (**If true, skip to step 8, else carry on**)
3. DNS lookup to find the IP address of the server
4. Browser initiates a TCP connection with the server
5. Browser sends an HTTP request to the server
6. Server handles the incoming request
7. Browser receives the HTTP response
8. Browser displays the HTML content  

# HyperText Transfer Protocol (HTTP)
- Client request consists of:
  - **REQUEST LINE**
    - Method name
    - Path of resource
    - HTTP version
  - **HEADER LINES**
    - Info about REQUEST
  - **(BODY)**
    - Uploaded files/info
- Server response:
  - **STATUS LINE**
    - HTTP version
    - Response code
    - Reason
  - **HEADER LINES**
    - Info about response
  - **(BODY)**
    - Returned file/info

## HTTP Request methods
- GET
- POST
- PUT
- DELETE
- HEAD
- CONNECT
- OPTIONS
- TRACE

# Three Tier Application Model
- **Presentation Tier (Front-end)**
  - Client
    - User Interface
- **Application Tier (Middleware)**
  - Web Server
    - Application Logic
- **Data Tier (Back-end)**
  - Database Server
    - Database and Storage
