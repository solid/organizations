Here's my proposed minimum shape for a Solid Storage Provider.  

The easiest way is to introduce new terms :

* `SolidStorageService` -  the storage provider 
* `SolidStorageServer` -  the server software used by the SolidStorageService

Here' a storage provider shape assuming these terms, aternates without the terms posted below. 

```turtle
<#openLink>
  schema:name "Open Link Read-Write Storage" ;
  a new:SolidStorageService ;
  doap:service-endpoint <https://solid.openlinsw.com:8444> ;
  schema:isFree "?" ;
  schema:provider [
    a schema:Organization ;
    schema:name "Open Link Software" ;
    schema:url <https://www.openlinksw.com/> 
  ] ;
  schema:softwareAddOn [
    schema:name "NSS Fork" ;      
    a new:SolidStorageServer ;
    doap:license "?" ;
    doap:repository <https://github.com/OpenLinkSoftware/node-solid-server> ;
  ] .
```

I am not happy with `schema:softwareAddon` any better ideaas?

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
