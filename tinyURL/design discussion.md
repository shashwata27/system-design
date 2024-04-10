1. what if short URLs never expire?
- add 4TB of storage every year, until all key exaughts i.e. 68B * 20kb = 13600TB
- Introduce "last accessed timestamp" in key-value DB for each key & expire them after X months. While informing user about expiry through mail.
   Updating last accessed can be heavy on DB, we can store logs of access and the time stamp then batch process logs to update the last accessed timestamp following
  event driven architecture. But this would introduce additional storage overhead.
