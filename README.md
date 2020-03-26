# HBase Database for Food Nutrition Facts

## Guide to setup Hbase with Docker

This guide is based on https://github.com/dajobe/hbase-docker, however we tweaked it a bit so we didn't have to configure our local DNS.

- 
- docker pull dajobe/hbase
- id=$(docker run --name=hbase-docker1 -h hbase-docker -d -p 16000:16000 -p 9090:9090 -p 8085:8085 -p 8080:8080 -p 2181:2181 -p 9095:9095 -p 16010:16010 dajobe/hbase)

Now you should be able to access the ports on localhost. (Some of them aren't accesible through the browser)
The above command syntax is bash.

Run the following command with the ID of the previously started container. (The ID variable)
- docker run --rm -it --link $id:hbase-docker dajobe/hbase hbase shell

Previous command should open a live terminal allowing you to execute hbase commands.

## Inserting data into Hbase

- First you must create the table manually in Hbase. run **create 'Food_Display_Table', 'cf'**
- Run the program.js (This will read the data from freeformatter-out.xml and insert it into Hbase)
- Now feel free to play with commands.

Examples 
```shell 
  scan 'Food_Display_Table', {FILTER => "ValueFilter (=,'binaryprefix:YOUR-SEARCH-VALUE')"} 
  scan 'Food_Display_Table', {FILTER=>"SingleColumnValueFilter('cf','ATTRIBUTE-NAME',=,'binary:ATTRIBUTE_VALUE')"} ```


