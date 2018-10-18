# Redis-Cluster

3-Master and 3-Slave Redis Distributed Cache. The topology is as below:

![](https://github.com/xxu10/Redis-Cluster/blob/master/images/Screen%20Shot%202018-10-18%20at%206.09.34%20PM.png)

First we need to build the cluster, instead of using redis-trib.rb, I used Lettuce (https://lettuce.io/) to do that. I opened 6 Redis instances to simulate 6 nodes in this cluster. After the bulid process, the cache will be ready to use.

![](https://github.com/xxu10/Redis-Cluster/blob/master/images/Screen%20Shot%202018-10-17%20at%208.31.45%20PM.png)

If one master node is offline, for example, the A-M, A-S will take the responsibility of A-M and become a master,
the cluser will change to:

![](https://github.com/xxu10/Redis-Cluster/blob/master/images/Screen%20Shot%202018-10-18%20at%206.31.43%20PM.png)

![](https://github.com/xxu10/Redis-Cluster/blob/master/images/Screen%20Shot%202018-10-17%20at%208.41.57%20PM.png)

![](https://github.com/xxu10/Redis-Cluster/blob/master/images/Screen%20Shot%202018-10-17%20at%208.42.08%20PM.png)

1. If A-M become alive in 5 seconds, the original A-M will be A-S this time,

![](https://github.com/xxu10/Redis-Cluster/blob/master/images/Screen%20Shot%202018-10-18%20at%206.39.36%20PM.png)

We need to balance the master and slave, just use clusterFailOver at A-M

2. If A-M is still offline after 5 seconds

