statsd-ctsdb-backend
============================

Tencent ctsdb backend for statsd

## Overview

This backend allows [Statsd][statsd] to save to [Elasticsearch][elasticsearch].  Supports dynamic index creation per day and follows the logstash naming convention of statsd-YYYY.MM.DD for index creation.

## History 

Originally written by Github user rameshpy, this library was created as a feature branch of etsy/statsd.  The statsd project recommended that this library be converted to its own repository as all other backends currently do.  This repository started as a restructuring of the existing feature branch into a standalone backend repository. Reconstructed from https://github.com/markkimsal/statsd-elasticsearch-backend


## Configuration

Merge the following configuration into your top-level existing configuration.
Add a structure to your configuration called "ctsdb"

```js

 backends: [ 'statsd-ctsdb-backend', 'other-backends'],
 debug: true,
 ctsdb: {
	 port:          9200,
	 host:          "localhost", // (e.g. https://service.tencentcs.com
	 path:          "/", 
         metrics: "", //ctsdb metrics 
         username: "",
         password: "",
	 indexPrefix:   "statsd",
	 //indexTimestamp: "year",  //for index statsd-2015 
	 //indexTimestamp: "month", //for index statsd-2015.01
	 indexTimestamp: "day",     //for index statsd-2015.01.01
	 countType:     "counter",
	 timerType:     "timer",
	 timerDataType: "timer_data",
	 gaugeDataType: "gauge",
     formatter:     "default_format"
 }
```
