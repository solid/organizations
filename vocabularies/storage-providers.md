Here's my proposed minimum shape for a Solid Storage Provider.  

The easiest way is to introduce new terms. I will provisionally use soar: as the prefix for these proposed terms - Solid Oraganizations and Resources vocabulary.

Here' a storage provider shape assuming some proposed terms, alternates without the terms posted below. 

```turtle
<#openLink>
  schema:name "Open Link Read-Write Storage" ;                  # the service
  a soar:SolidStorageService ;
  doap:service-endpoint <https://solid.openlinsw.com:8444> ;
  schema:isFree "?" ;
  schema:provider [
    schema:name "Open Link Software" ;                           # the providing organization
    a schema:Organization, soar:SolidStorageProvider ;
    schema:url <https://www.openlinksw.com/> 
  ] ;
  soar:implementedUsing [
    schema:name "NSS Fork" ;                                     # the software 
    a soar:SolidStorageServer ;
    doap:license "?" ;
    doap:repository <https://github.com/OpenLinkSoftware/node-solid-server> ;
  ] .
```

If we do not use the proposed new terms, this is the closest I can come to replacing them
using the [product ontology](http://www.productontology.org/).

  Instead of SolidStorageService
  ```turtle
    [
       a schema:Service, doap:Project ;
       schema:additionalType pto:Storage_Server ;
       doap:implements <https://solidproject.org/TR/Protocol.html> 
    ]
  ```
  Instead of SolidStorageServer
  ```turtle
    [
       a doap:Project ; a schema:SoftwareApplication ;
       schema:additionalType pto:Storage_Server ;
       doap:implements <https://solidproject.org/TR/Protocol.html> 
    ]
  ```
     
If OpenLink also offers an IdP service, we'd need similar predicates for them, else use pto:Identity_Server.   
