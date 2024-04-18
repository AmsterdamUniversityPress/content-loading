# Proxy

First of all, a "proxy" is a **server** that sits between a client requesting a resource (e.g. your computer when you click on a DOI to go to an article and read or download it) and a server hosting that resource (in this example, the article). Proxy servers are used to provide privacy, security, and performance.

So, instead of connecting directly to the reosurce, the client directs the request to the proxy server. The proxy server in its turn connects to the resource and passes the information back to the client. That is why it is sometimes called "middleware".

In academic publishing, proxy servers are used to provide federated access. This is how it works: a client sits outside the university's or libraries network. The client contacts the proxy and is authenticated. The proxy then accesses the resource to which the organization subscribes.

## EZProxy 

The oldest and probably best known example is [EZProxy](https://amsterdamuniversitypress.github.io/content-loading/ezproxy), created in 1999. It is now a service provided by OCLC. EZProxy works by dynamically altering the URLs of the resources to match the proxy's URL, so that the client only access the proxy. 

- https://www.oclc.org/en/ezproxy.html

## EZProxy on Edify

Edify supports authentication through EZProxy. Institutional administrators can add the IP addresses for their proxy servers into the IP address section. AUP administrators can also do that for the institutional accounts through the user management tool.

Institutional administrators should also set up the following stanza in their EZProxy configuration file.

```
T Amsterdam University Press Online
U https://www.aup-online.com/
H www.aup-online.com
NeverProxy instance.metastore.ingenta.com
NeverProxy pub2web.metastore.ingenta.com
```

On a related note, you can also submit a request to OCLC to get the EZProxy stanza added to their list. [Here](https://help.oclc.org/Library_Management/EZproxy/EZproxy_database_stanzas/Database_stanzas_I/Intellect_Discover) is an example of an EZProxy stanza on the OCLC site for the Intellect Discover Edify site.

[Here](https://help-nl.oclc.org/Library_Management/EZproxy/EZproxy_database_stanzas/Database_stanzas_B/BrillOnline | BrillOnline Stanzas) is an example of the stanza of another publisher. In order to provide access to resources that use https, your EZproxy server must be configured with an [SSL certificate](https://help-nl.oclc.org/Library_Management/EZproxy/Secure_your_EZproxy_server/010SSL_configuration). This is the case  for Edify.

## OpenAthens
[OpenAthens][(https://amsterdamuniversitypress.github.io/content-loading/openathens) assigns a unique proxy IP address to each customer. Only valid users from this institution will be able to
authenticate via this proxy IP address.

## OpenAthens on Edify
...

## Alternatives
Nowadays alternatives exist

- [Shibboleth](https://amsterdamuniversitypress.github.io/content-loading/shibboleth)
- [Open Authentication](https://amsterdamuniversitypress.github.io/content-loading/openauthentication)

