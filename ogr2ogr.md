# ogr2ogr


## Geographies for CSV files

To get geographies in CSV files, you have to specify the format using the
`-lco` flag. Specifically, using something like `-lco GEOMETRY=AS_WKT` is good
for data that will go into BigQuery.


## Show progress

The `-progress` flag prints the progress of the conversion
