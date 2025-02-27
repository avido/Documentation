# REST API: POST collection fields

Methode om een veld toe te voegen aan een bestaande collectie. Dit is een HTTP 
POST call naar het volgende adres:

`https://api.copernica.com/v3/collection/$id/fields?access_token=xxxx`

De code `$id` moet je vervangen door de numerieke identifier van de collectie
waar je een veld aan wilt toevoegen. De naam van het veld, en eventuele
andere waardes moeten als message body aan het HTTP request worden toegevoegd.

## Beschikbare parameters

De volgende variabelen kunnen in de body van de HTTP POST call worden geplaatst.

* **name**: Naam van het nieuw aan te maken veld (verplicht)
* **type**: Type van het nieuwe veld
* **value**: Standaardwaarde van het nieuwe veld
* **textlines**: Voor tekstvelden: het aantal regels in formulieren om het veld te bewerken
* **length**: Maximum lengte voor teksten
* **index**: Boolean waarde of een index op het veld moet worden aangemaakt
* **displayed**: Boolean waarde om aan te geven dat het veld in de user interface in lijsten en grids moet worden geplaatst
* **hidden**: Boolean waarde om aan te geven dat een veld nooit zichtbaar mag zijn in de user interface
* **ordered**: Boolean waarde of profielen standaard op basis van dit veld zijn gesorteerd

Een veld kan de volgende types hebben:

* **integer**: numerieke waarde
* **float**: numeriek *floating point* nummer ("komma-getal")
* **date**: datumveld dat verplicht moet zijn ingevuld
* **empty_data**: datumveld dat ook leeg gelaten mag worden
* **datetime**: veld met datum + tijdstip dat moet zijn ingevuld
* **empty_datetime**: veld met datum + tijdstip dat leeg mag worden gelaten
* **text**: regulier tekstveld
* **email**: veld met een e-mailadres dat wordt gebruikt voor mailings (maximaal 1 per database)
* **phone**: telefoonveld
* **phone_fax**: telefoonveld met faxnummer dat kan worden gebruikt voor faxmailings (maximaal 1 per database)
* **phone_gsm**: telefoonveld met mobiel nummer dat kan worden gebruikt voor sms berichten (maximaal 1 per database)
* **select**: meerkeuzeveld
* **big**: groot tekstveld
* **foreign_key**: numerieke waarde met verwijzing naar ander profiel

## Voorbeeld in PHP

Het volgende PHP script demonstreert hoe je de API methode kunt aanroepen:

```php
// dependencies
require_once('copernica_rest_api.php');

// change this into your access token
$api = new CopernicaRestAPI("your-access-token", 3);

// data to pass to the call
$data = array(
    'name'      =>  'extra-veld',
    'type'      =>  'text'
);

// do the call
$api->post("collection/{$collectieID}/fields", $data);
```

Dit voorbeeld vereist de [REST API klasse](rest-php).

## Meer informatie

* [Overzicht van alle API calls](rest-api)
* [Alle velden van een collectie opvragen](rest-get-collection-fields)
* [Veld bijwerken](rest-put-collection-field)
* [Veld verwijderen](rest-delete-collection-field)
