# StockSynchronizer

De StockUpdateSynchronizer is op dezelfde manier opgebouwd als de andere synchronizers.

Momenteel werkt de StockUpdateSynchronizer nog NIET samen met MultiSource Inventory (MSI).

1. `StockUpdateProviderInterface` haalt stock-updates op uit de bron
2. `StockUpdateStorageInterface` werkt de opgehaalde stock-updates bij in Magento

## Implementatie

### StockUpdateProviderInterface

De huidige implementatie van de `StockUpdateProviderInterface` is `Webwijs\M2MplusSynchronizer\Stock\MplusDefaultStockUpdateProvider`.

Deze provider haalt de laatste voorraad in absolute aantallen op uit de MplusKassa API. Zonder argumenten mee te geven haalt deze provider alleen de voorraad op die gewijzigd is sinds de laatste "Stock ID". 
Dit werkt op dezelfde manier als de SyncMarkers van de product synchronizer en wordt ook in dezelfde tabel bijgehouden.

Het is ook mogelijk om een lijst van SKU's mee te geven om alleen de voorraad van specifieke producten bij te werken.

### StockUpdateStorageInterface

De huidige implementatie van de `StockUpdateStorageInterface` is `Webwijs\M2ProductSynchronizer\Stock\DefaultDbStockUpdateStorage`.

Deze implementatie slaat de voorraadupdates rechtstreeks op in de database via "kale" SQL queries.
