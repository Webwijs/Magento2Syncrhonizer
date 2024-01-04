# ProductSynchronizer

Het synchroniseren van producten gebeurt in een aantal stappen, hieronder beschreven.

```mermaid
graph TD; 
    id1[1. ProductProviderInterface] --> 
    id8[/ProductCollection/] --> 
    id2[2. ProductAttributeResolverInterface] -->
    id8[/ProductCollection/] -->
    id3[3. ProductStorageInterface] -->
    id8[/ProductCollection/] -->
    id4[4. ImageImportInterface] -->
    id8[/ProductCollection/] -->
    id5[5. ProductConfigurableConnectInterface] -->
    id8[/ProductCollection/] -->
    id6[6. ProductSiteConnectorInterface] -->
    id8[/ProductCollection/] -->
    id7[7. StockUpdateSynchronizerInterface] -->
    id8[/ProductCollection/]
```

1. De **ProductProviderInterface** haalt de productgegevens op uit de bron, bijvoorbeeld een kassasysteem of een PIM. Hij maakt voor de opgehaalde productinformatie een ProductCollection object aan dat gevuld wordt met alle informatie die nodig is om de producten te importeren in Magento 2.
2. De **ProductAttributeResolverInterface** vormt de waardes van de aangeleverde attributen om naar de daadwerkelijke attributen in Magento. Bijvoorbeeld de **categorie ID's, BTW-klassen, kleuren en maten**.
3. De **ProductStorageInterface** slaat de producten op in de **database** van Magento 2.
4. De **ImageImportInterface** importeert de afbeeldingen van de producten.
5. De **ProductConfigurableConnectInterface** verbindt de simpele producten met de configureerbare producten.
6. De **ProductSiteConnectorInterface** verbindt de producten met de juiste websites
7. De **StockUpdateSynchronizerInterface** voert een initiële voorraadupdate uit voor de zojuist geïmporteerde producten.

