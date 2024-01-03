Endpoints
=====

Er zijn 2 endpoints die in de PricingManager ingesteld kunnen worden. 
* Update
* Delete

Update
------------
Het Update endpoint zorgt er voor dat wanneer een product in de PricingManager aangepast wordt, dit direct wordt doorgezet naar de Wordpress omgeving. 

Voor Frieslandlease is dit endpoint: `https://www.frieslandlease.nl/autodisk/update`

> **_NOTE:_** Dit update endpoint staat op moment van schrijven uit, aangezien de 
afbeelding formaten niet correct worden doorgegeven.

Delete
------------
Het Delete endpoint zorgt ervoor dat wanneer een product in de PricingManager verwijderd wordt, dat dit product ook in de Wordpress omgeving verwijderd wordt.

Daarnaast wordt de productdata die opgeslagen staat in de Database verwijderd en ook de productafbeeldingen worden verwijderd.

Voor Frieslandlease is dit endpoint: `https://www.frieslandlease.nl/autodisk/delete` 
