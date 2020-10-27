# Stream-Processing-of-Twitter-Data-using-Apache-Spark
Saving streaming data to persistence storage, Accessing RDD inside a DStream, RDD partitioning, RDD catching

stateful transformation
Spark streaming uses a micro batch architecture where the incoming data is grouped into micro batches 
called Discretized Streams (DStreams) which also serves as the basic programming abstraction. 
The DStreams internally have Resilient Distributed Datasets (RDD) and as a result of this standard 
RDD transformations and actions can be done.


Window transformations are specific to Spark Streaming because they operate on a set of X recent RDDs. 
The X parameter tells on how many items (RDDs) we want to work. If instead of X we put 3 seconds, 
it means that the 3 last seconds of data will be taken into account. 
Specifically in Spark Streaming this parameter is called window duration.


window transformation allow you to compute results across a longer time period than batch interval.

Example - top selllers from ast hour
	you might process data every 1 sec(batch interval),
	but maintain a window for 1 hour
The windo slides as times goes on, to represent batched within the window interval.

