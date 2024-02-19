# OrderExportSynchronizer

De order export synchronizer exporteert orders vanuit Magento naar externe systemen zoals de MplusKassa API.

Hij is wederom in dezelfde structuur opgebouwd als de ProductSynchronizer, alleen nu de andere kant op. 

1. De `OrderExportProviderInterface` is verantwoordelijk voor het ophalen van (nieuwe) bestellingen uit Magento.
2. De `OrderExportProviderInterface` is verantwoordelijk voor het exporteren van de order naar het externe systeem.

## Implementatie

### OrderExportProviderInterface

De huidige implementatie van de `OrderExportProviderInterface` is `Webwijs\M2Synchronizer\Order\Export\OrderExportProvider`.

Deze provider haalt bestellingen met de status `processing` op uit Magento. Hij filtert nog op een extra attribuut, namelijk `external_id`. Als dit veld NULL is weet de provider dat deze order nog niet geëxporteerd is.

### OrderExportStorageInterface

De huidige implementatie van de `OrderExportProviderInterface` is `Webwijs\M2MplusSynchronizer\Order\Export\MplusOrderExportStorage`.

Deze class is verantwoordelijk voor het exporteren van de nieuwe orders naar de MplusKassa API.

Bij MplusKassa is het verplicht om een klantnummer mee te sturen met een order. Deze order export storage kijkt dus eerst of er een klantnummer gevonden wordt in de API, met het betreffende e-mailadres.

Als dit het geval is wordt het bestaande klantnummer meegestuurd met de order. Als dit niet het geval is, wordt er eerst een nieuwe klant aangemaakt aan de hand van de gegevens uit de bestelling. Waarna dat klantnummer wordt meegegeven aan de order.

## Gebruik

Deze synchronizer wordt net al de rest aangeroepen via een CLI-commando. 

Als er geen argumenten worden meegegeven worden alleen nieuwe orders (status=processing, external_id=null) verwerkt.

`php bin/magento synchronizer:order-export`

Als argument kan er ook nog een order-id meegegeven worden. Dan wordt alleen deze order geëxporteerd, status en external_id worden dan genegeerd.

`php bin/magento synchronizer:order-export --order-id=200004556654`
