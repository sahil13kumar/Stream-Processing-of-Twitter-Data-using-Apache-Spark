# Notes
Saving streaming data to persistence storage, Accessing RDD inside a DStream, RDD partitioning, RDD catching

## stateful transformation
Spark streaming uses a micro batch architecture where the incoming data is grouped into micro batches 
called Discretized Streams (DStreams) which also serves as the basic programming abstraction. 
The DStreams internally have Resilient Distributed Datasets (RDD) and as a result of this standard 
RDD transformations and actions can be done.


## Window transformations 
window transformation allow you to compute results across a longer time period than batch interval. \
Example - top selllers from ast hour
- you might process data every 1 sec(batch interval),
- but maintain a window for 1 hour \
The window slides as times goes on, to represent batched within the window interval.

### Spark Streaming Checkpoint
A process of writing received records at checkpoint intervals to HDFS is checkpointing. 


## Deaking with driver script failure
Instead of working with StreaminContext you created directly, use the one returned by
StreamingContext.getOrCreate(checkpointDir, <function that create a new StreamingContext>)
 - takes a checkpoint directory as well fuction that will crate a new streaming context
 - First check checkpoint directory and see if something was left over there from previous driver run that 
   terminated unexpectedly and if so it can just pick up from where it left of.

Then if you need to restart your driver script, it can pick up frrom the checkpointing directory.
Still need to monitor the driver node for failure, and restart the script if it does
