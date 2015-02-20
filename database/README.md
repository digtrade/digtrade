
The Trading Consequences database contains the text mining output for the last round of processing completed for the project in December 2013 and is the back-end to all of the [online visualisations](http://tradingconsequences.blogs.edina.ac.uk/access-the-data/) to make it more accessible to historians and other users.  We provide a download of the database for anyone who would like to work directly with the database.

**Download**

The Trading Consequences database archive can be downloaded here:

[http://tcqdev.edina.ac.uk/trcons.backup.tar.gz](http://tcqdev.edina.ac.uk/trcons.backup.tar.gz)

It is approx. 8GB in size and needs to be unarchived first using tar (it will then be approx. 50GB).


**Restoring the Database**

To restore the database we recommend creating a new postgres database, install the PostGIS extension <http://postgis.net> to the newly created database and then use ``pg_restore`` to restore from the backup file using the following options:

```pg_restore -e -Fc -d <dbname> trcons.backup```

where ``<dbname>`` is the database you have created. Once restored and the indexes have finished building the database should be approx. 80GB in size.

**Database Content**

The database contains the following tables:

Documents: information about 200,871 documents including document title, author, publication year, collection, and a URL to the original digitized document.

Commodity Mentions: all mentions of each commodity (currently 28,595,550) reproducing exactly the spelling of the commodity in the text. Each commodity mention is linked to the corresponding document, the page identifier, the sentence snippet from which it was extracted, and the corresponding DBpedia concepts and categories. The latter helps to categorize, for example, commodity mentions that refer to the same commodity but are spelled differently.

Location Mentions: all location mentions along with their corresponding document, page identifier, and sentence snippet. Furthermore, we store their latitude/longitude coordinates and GeoNames identifier. There are currently 74,744,515 location mentions stored in the database, corresponding to 2,275,186 unique locations identified in the corpus.

Commodity-Location Relations: the text mining component identified a total of 13,969,659 commodity-location relations across the entire document corpus which are stored in this additional table.  Each commodity-location pair is linked to the corresponding commodity/location mentions tables via identifiers to enrich them with additional information such as the corresponding document, sentence snippet, commodity concept, and latitude and longitude.