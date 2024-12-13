# DOI Registration

The platform performs a task called _distribution_. This means it sends metadata and content to specified third parties. The site admin can set this up. 

One distribution line set up is to CrossRef. It has at least two purposes: DOI registration and retrieval of references. The latter will be dealt elsewhere on these pages. This page deals with DOI registration.

First, it is good to know that DOIs can be created by anyone (as long as they comply with the specifications). Their _registration_ however, is in the hand of a few third parties, and CrossRef is undoubtedly the most prominent one. 

CrossRef makes sures the DOI resolves to a URL. To that end, the publisher has to submit metadata to CrossRef. (With that metadata, CrossRef performs a lot of other functions as well, like tracking references to content items in other content items).

This task is performed by Edify. The platform takes the metadata (in JATS or BITS XML), and transforms it into another type of XML that CrossRef can understand, and sends it to CrossRef. 

CrossRef then either registers the DOI, or returns an error message. 

These error message take the form of emails that are sent to the Support mailbox at AUP. (The site admin can choose where they are sent).

There is currently no procedure for dealing with these error message, and no one is dealing with them. This needs too change, but how?
