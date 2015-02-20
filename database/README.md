The Trading Consequences database archive can be downloaded here:

<a href="http://tcqdev.edina.ac.uk/trcons.backup.tar.gz">http://tcqdev.edina.ac.uk/trcons.backup.tar.gz</a>

It is approx. 8GB in size and needs to be unarchived first using tar (it will then be approx. 50GB).

To restore the database we recommend creating a new postgres database, install the PostGIS extension <http://postgis.net> to the newly created database and then use ``pg_restore`` to restore from the backup file using the following options:

```pg_restore -e -Fc -d <dbname> trcons.backup```

where <dbname> is the database you have created. Once restored and the indexes have finished building the database should be approx. 80GB in size.