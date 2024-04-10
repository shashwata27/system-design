# Core Features
- input long link, outputs short link
- when clicked on short link redirects to long link

# Addtional Features
- link history, all registered users can see the links they created
- link expiration, after 5 years
- number of clicks on each link

# Out of scope
- user management

# NFRs
- 99.999% avaibility
- scaleable (redirection speed shouldn't increase with more users)
- minimum latency

# Quantifying Scale
- DAUs? 100M
- Spike Events? No
- Interaction per user? 1click/day
- read/write ratio? 10:1
- avg long URL length? 200chars=200bytes
- replication factor? None=1

# Eastimation
- read: 1 click per day * 10^8 DAU = 10^8 read/day = 10^(8-5) read/sec = 10^3 read/sec
- write: 10^2 write/sec
- read bandwidth: 10^3 RPS * 200 bytes =  10^3 * 2 * 10^2 bytes/sec = 2 * 10^5 * 10^-3 kb/s = 200 kb/sec
- write bandwidth: 20kb/sec
- storage (5 years): 20 kb/sec * 2 * 10^8 sec = 4 * 10^9 * 10^-6 GB/s = 4 * 10^3 GB/s = 4000 GB = 4 TB
