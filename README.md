Apache Phoenix on Docker
==============

A Docker image to quick start [Apache Phoenix](http://phoenix.apache.org/) on [Apache HBase](https://hbase.apache.org/)
to provide an SQL interface. This image uses the Phoenix Avatica queryserver to allow thin clients to communicate via REST requests over wire protocol.

Apache Phoenix is a SQL skin over HBase delivered as a client-embedded JDBC driver targeting low latency queries over HBase data. Apache Phoenix takes your SQL query, compiles it into a series of HBase scans, and orchestrates the running of those scans to produce regular JDBC result sets. The table metadata is stored in an HBase table and versioned, such that snapshot queries over prior versions will automatically use the correct schema. Direct use of the HBase API, along with coprocessors and custom filters, results in performance on the order of milliseconds for small queries, or seconds for tens of millions of rows.

###Versions
Apache Hadoop - 2.7.0  
Apache HBase - 1.0.x, 1.1.x
Apache Phoenix - 4.4.0+

###Launch
The queryserver can be accessed via the host ip and the port 8765.
####Foreground
`docker run -it --name phoenix -p 8765:8765 kliew/phoenix-queryserver`

####Background
`docker run -d --name phoenix -p 8765:8765 kliew/phoenix-queryserver`

###sqlline
`docker exec -it phoenix -sqlline`

### Build
Docker 1.10 or higher is required to build the image (to use `--build-arg`).

To build a specific version
```
docker build -t kliew/phoenix-queryserver --build-arg PHOENIX_VERSION=4.7.0 .
```

#### Build Parameters
* PHOENIX_VERSION
* HBASE_MAJORMINOR
* HBASE_PATCH
* ZOOKEEPER_VERSION
