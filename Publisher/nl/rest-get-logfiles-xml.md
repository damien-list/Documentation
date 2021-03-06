# REST API: GET logfiles .xml

Copernica houdt logfiles bij die je op kunt vragen met de API. 
Deze methode kan gebruikt worden om een logfile op te vragen als een CSV 
bestand met de bestandsnaam. Instructies voor het opvragen van een bestandsnaam 
kun je vinden onder het kopje "Meer informatie". Om de methode aan te roepen 
verstuur je een HTTP GET verzoek naar de volgende URL:

`https://api.copernica.com/v1/logfiles/$filename/xml?access_token=xxxx`

Hier moet je `$filename` vervangen door de bestandsnaam.


## Teruggegeven bestand

Deze functie geeft een XML representatie van de opgevraagde logfile terug.
Er volgt nu een voorbeeld van hoe zo'n representatie eruit ziet.

```xml
<records>
    <record>
        <id>XXXXXXXXXX1</id>
        <time>2016-11-04 11:01:00</time>
        <mailingid>12345</mailingid>
        <profileid>1111111</profileid>
        <subprofileid>2</subprofileid>
        <databaseid>133</databaseid>
        <collectionid>0</collectionid>
        <senderdomain>copernica.com</senderdomain>
        <templateid>1234</templateid>
        <tags></tags>
        <email>employee1234@copernica.com</email>
    </record>
    <record>
        ...
    </record>
    ...
</records>
```

## Voorbeeld in PHP

Het volgende PHP script demonstreert hoe je de API methode gebruikt.

```php
    // vereiste scripts
    require_once('copernica_rest_api.php');
    
    // verander dit naar je access token
    $api = new CopernicaRestApi("your-access-token");

    // voer het verzoek uit en print het resultaat
    print_r($api->get("logfiles/cdm-attempts.2016-11-04.log/xml"));
```

Dit voorbeeld vereist de [REST API class](rest-php).


## Meer informatie

* [Overzicht van alle API calls](./rest-api.md)
* [GET logfiles names](./rest-get-logfiles-names.md)
* [GET logfiles JSON](rest-get-logfiles-json)
* [GET logfiles CSV](rest-get-logfiles-csv)
