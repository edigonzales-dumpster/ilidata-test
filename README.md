# ilidata-test

```
docker run --rm --name edit-db -p 54321:5432 --hostname primary -e PG_DATABASE=edit -e PG_LOCALE=de_CH.UTF-8 -e PG_PRIMARY_PORT=5432 -e PG_MODE=primary -e PG_USER=admin -e PG_PASSWORD=admin -e PG_PRIMARY_USER=repl -e PG_PRIMARY_PASSWORD=repl -e PG_ROOT_PASSWORD=secret -e PG_WRITE_USER=gretl -e PG_WRITE_PASSWORD=gretl -e PG_READ_USER=ogc_server -e PG_READ_PASSWORD=ogc_server sogis/oereb-db:latest
```

```
java -jar /opt/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --dbschema agi_metadb_ilidata --nameByTopic --createEnumTabs --beautifyEnumDispName --createMetaInfo --createFk --createFkIdx --createUnique --createNumChecks --models DatasetIdx16 --schemaimport


java -jar /opt/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --dbschema agi_metadb_ilidata --nameByTopic --createEnumTabs --beautifyEnumDispName --createMetaInfo --createFk --createFkIdx --createUnique --createNumChecks --models DatasetIdx16 --disableValidation --export fubar2.xtf

java -jar /opt/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --dbschema agi_metadb_ilidata --nameByTopic --createEnumTabs --beautifyEnumDispName --createMetaInfo --createFk --createFkIdx --createUnique --createNumChecks --models DatasetIdx16 --disableValidation --createBasketCol --importBid --createTidCol --importTid --doSchemaImport --import fubar.xtf


java -jar /Users/stefan/apps/ili2pg-4.4.2/ili2pg-4.4.2.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --dbschema agi_metadb_ilidata --nameByTopic --createEnumTabs --beautifyEnumDispName --createMetaInfo --createFk --createFkIdx --createUnique --createNumChecks --models DatasetIdx16 --disableValidation --createBasketCol --importBid --createTidCol --importTid --doSchemaImport --import ilidata.xml

java -jar /Users/stefan/apps/ili2pg-4.4.2/ili2pg-4.4.2.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --dbschema agi_metadb_ilidata --nameByTopic --createEnumTabs --beautifyEnumDispName --createMetaInfo --createFk --createFkIdx --createUnique --createNumChecks --models DatasetIdx16  --doSchemaImport --noSmartMapping --import fubar.xtf

java -jar /Users/stefan/apps/ili2pg-4.4.2/ili2pg-4.4.2.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --dbschema agi_metadb_ilidata --nameByTopic --createEnumTabs --beautifyEnumDispName --createMetaInfo --createFk --createFkIdx --createUnique --createNumChecks --models DatasetIdx16 --export fubar_export.xtf

```


```
SELECT 
    bfsnr, 
    st_xmin(st_transform(grenze.geometrie, 4326)), 
    st_ymin(st_transform(grenze.geometrie, 4326)), 
    st_xmax(st_transform(grenze.geometrie, 4326)), 
    st_ymax(st_transform(grenze.geometrie, 4326)) 
FROM 
    live.dm01vch24lv95dgemeindegrenzen_gemeinde AS gemeinde
    LEFT JOIN live.dm01vch24lv95dgemeindegrenzen_gemeindegrenze  AS grenze
    ON grenze.gemeindegrenze_von = gemeinde.t_id 
WHERE   
    bfsnr IN (2401, 2403, 2405, 2407, 2408, 2455, 2456, 2457, 2473, 2474, 2475, 2476, 2477, 2479, 2491, 2498, 2501, 2502, 2514, 2551, 2573, 2580, 2581, 2586, 2613, 2614, 2615, 2516)
ORDER BY 
    bfsnr 
```