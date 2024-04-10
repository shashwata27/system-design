# what if short URLs never expire?
- add 4TB of storage every year, until all key exaughts i.e. 68B * 20kb = 13600TB
- Introduce "last accessed timestamp" in key-value DB for each key & expire them after X months. While informing user about expiry through mail.
   Updating last accessed can be heavy on DB, we can store logs of access and the time stamp then batch process logs to update the last accessed timestamp following
  event driven architecture. But this would introduce additional storage overhead.

# Key Gen Service Single Point of Failure?
- Spin up multiple instances of service with load balancer and shard the orginal DB into chunks with each service attached to only one of the chunks. Dividing the key range enures data consistency
- If we switch the DB type to NoSQL and use mongoDB it has a single master node write architecture. which handles data consistency issues for multiple nodes.
- We can also use snowflake algo to gen 18char strings as IDs which will be gaurenteed to be unique even accross multiple nodes running paralelly.
