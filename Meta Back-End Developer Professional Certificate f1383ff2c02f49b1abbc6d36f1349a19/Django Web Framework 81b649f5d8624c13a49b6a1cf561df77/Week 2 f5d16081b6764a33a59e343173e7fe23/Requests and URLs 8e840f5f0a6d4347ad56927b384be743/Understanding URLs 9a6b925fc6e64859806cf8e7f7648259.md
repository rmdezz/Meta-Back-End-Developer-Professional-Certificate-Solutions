# Understanding URLs

# Introduction

In this video, you will learn about uniform resource locators (URLs) and the different parts that make up a URL. You will discover how each URL is purposefully constructed to point to a specific resource or web page on the web.

# What is a URL?

Every time you click on a web link or type in a web address, you visit a URL. A URL is made up of multiple parts put together. These include the scheme, domain name, file path, and parameters.

## Scheme (Protocol)

- The first part of a URL is the scheme or otherwise referred to as the protocol. It's located at the beginning of any ural address and can be identified as HTTP or HTTPS.
- The characters HTTP stands for hypertext transfer protocol.
- The protocol determines the set of rules around the transmission and exchange of data.
- The difference between HTTP and HTTPS is security as the S stands for secure.
- HTTP sends data as plain text which can expose the sender's information HTTPS encrypts all data. This means the data isn't in a readable format which is more secure. The HTTP protocol is also responsible for sending and receiving HTML across the web.
- HTTP and its extension HTTPS is the most widely used protocol over the web.

## Subdomain

The subdomain is located before the domain and usually contains the home page and other important pages. 

The most common subdomain is World Wide Web represented by **[WWW](http://www/)**. It's important to know that some browsers replace the scheme and subdomain with a symbol such as that of a lock for encrypted pages. This is done to make the URLs easier to read and understand.

## Domain name

Next is the domain name which consists of two parts: the second-level domain and top-level domain. 

- The second-level domain name refers to an organization or the name of a company. For example, the second-level domain for the company called Little Lemon is Little Lemon.
- The part that follows the second-level domain and concludes your domain name is called the top-level domain. It is used to reference a country or category of your organization. For example, a .com address can indicate a commercial entity, .org means an organization, and .ie represents a country, sovereign state or dependent territory.

## File path

The file path, also known as the page path, directs you to the location of a resource. 

The resource may be any type of files that can be transmitted over HTTP, such as web documents, image files, and metadata. 

It's worth remembering that a URL is simply an address where the files are stored. They can either be local or web-based, which can be external to the domain. 

When hosting locally, the resources such as images and web files are located on the user's device or server.

When web-based, they exist on the user's remote web server or external server. For example, the web-based URL for the 4.1 release for Django has its own URL with a specific file path which includes the year, month and day it was published.

## URL Parameters

URL parameters are also known as query strings and are used to structure additional information inside a URL. You use URL parameters to capture any part of the URL and pass its value for processing. A query string is similar. It begins with a question mark symbol and is placed after the URL path. It contains parameters represented as key-value pairs that can appear inside a URL path.