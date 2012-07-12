The Yetti webservice API
========================

Yetti is a web-based Software as a Service (SaaS) e-commerce and publishing platform.
In addition to the built in administration tools, Yetti allows users to manage content via a simple web service (ReST: Representational State Transfer) interface.

For more details on Yetti, please refer to http://yetti.co.uk. We welcome comments, feedback and bug reports at support@yetti.co.uk.

Intended audience
-----------------

This guide is intended to assist software developers who want to write applications using the Yetti API.
To use the information provided here, you should first have a general understanding of the Yetti platform and have access to an active administration account with web service credentials. 
You should also be familiar with:

* ReSTful web services
* HTTP/1.1
* XML and/or JSON data serialization formats

Concepts
========

To use the Yetti API effectively, you should understand several key concepts:

Authentication
--------------

Authentication is the process of proving your identity to the system. 
Identity is an important factor when performing web service requests, as it is your identify which governs what access you have and what operations you are allowed to perform.

Some basic Yetti API operations don't require authentication, however any method which alters data, and most which return data specific to your system do require particular privileges. 
The authentication and signing process is explained in more detail in section 3.1.

Resources
---------

Most individual pieces of content in Yetti are known as “resources”. Resources can usually be created, updated and deleted, unless specific permissions dictate otherwise.

