# ilidata-test

```
docker run --rm --name edit-db -p 54321:5432 --hostname primary -e PG_DATABASE=edit -e PG_LOCALE=de_CH.UTF-8 -e PG_PRIMARY_PORT=5432 -e PG_MODE=primary -e PG_USER=admin -e PG_PASSWORD=admin -e PG_PRIMARY_USER=repl -e PG_PRIMARY_PASSWORD=repl -e PG_ROOT_PASSWORD=secret -e PG_WRITE_USER=gretl -e PG_WRITE_PASSWORD=gretl -e PG_READ_USER=ogc_server -e PG_READ_PASSWORD=ogc_server sogis/oereb-db:latest
```

```
java -jar /opt/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --dbschema agi_metadb_ilidata --nameByTopic --createEnumTabs --beautifyEnumDispName --createMetaInfo --createFk --createFkIdx --createUnique --createNumChecks --models DatasetIdx16 --schemaimport


java -jar /opt/ili2pg-4.3.1/ili2pg-4.3.1.jar --dbhost localhost --dbport 54321 --dbdatabase edit --dbusr admin --dbpwd admin --dbschema agi_metadb_ilidata --nameByTopic --createEnumTabs --beautifyEnumDispName --createMetaInfo --createFk --createFkIdx --createUnique --createNumChecks --models DatasetIdx16 --disableValidation --export fubar.xtf
```