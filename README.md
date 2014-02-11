

THIS DOCUMENT IS UNDER ONGOING WORK AND IS VERY PARTIAL AND INITIAL
===

HadoopCoin
===

Overview
---

The purpose of this document is to describe a distributed ecosystem which spreads general computational work among client platforms, and getting paid for that work via a dedicated coin.

Hadoop (by Apache foundation) is an open source distributed computing engine.

The Vision
---

Distributed Big-Data (Data-Mining) computing is so growing that it can be said it is the main buzz on the software world over the recent few years. Companies, researchers and developers need more and more giant computational power. Such entities either buy hardware or rent servers. Why would they do so, if, roughly speaking, mobile phones around the world can perform the same tasks in a stronger and more secure manner (since we are talking about a distributed decentralized system), and the payment for the computing service is spread among the crowd other than on centralized hands? If the Blockchain algorithm can take the control of financial transfers and pass it to the public, so can be done to cloud computing.

We therefore imagine a world with no hosting companies. Only distributed autonomous corporations (DACs, as by Invictus Innovations) will instantly serve every company, researcher and so on.

Some Hadoop Highlights from Wikipedia
---

Apache Hadoop is an open-source software framework for storage and large scale processing of data-sets on clusters of commodity hardware. Hadoop is an Apache top-level project being built and used by a global community of contributors and users.[2] It is licensed under the Apache License 2.0.
The Apache Hadoop framework is composed of the following modules :
* Hadoop Common - contains libraries and utilities needed by other Hadoop modules
* Hadoop Distributed File System (HDFS) - a distributed file-system that stores data on the commodity machines, providing very high aggregate bandwidth across the cluster.
* Hadoop YARN - a resource-management platform responsible for managing compute resources in clusters and using them for scheduling of users'' applications.
* Hadoop MapReduce - a programming model for large scale data processing.
All the modules in Hadoop are designed with a fundamental assumption that hardware failures (of individual machines, or racks of machines) are common and thus should be automatically handled in software by the framework. Apache Hadoop''s MapReduce and HDFS components originally derived respectively from Google''s MapReduce and Google File System (GFS) papers.
Beyond HDFS, YARN and MapReduce, the entire Apache Hadoop “platform” is now commonly considered to consist of a number of related projects as well – Apache Pig, Apache Hive, Apache HBase, and others.[3]
For the end-users, though MapReduce Java code is common, any programming language can be used with "Hadoop Streaming" to implement the "map" and "reduce" parts of the user''s program.[4] Apache Pig, Apache Hive among other related projects expose higher level user interfaces like Pig latin and a SQL variant respectively. The Hadoop framework itself is mostly written in the Java programming language, with some native code in C and command line utilities written as shell-scripts.
Apache Hadoop is a registered trademark of the Apache Software Foundation.

Hadoop consists of the Hadoop Common package, which provides filesystem and OS level abstractions, a MapReduce engine (either MapReduce/MR1 or YARN/MR2)[9] and the Hadoop Distributed File System (HDFS). The Hadoop Common package contains the necessary Java ARchive (JAR) files and scripts needed to start Hadoop. The package also provides source code, documentation and a contribution section that includes projects from the Hadoop Community.
For effective scheduling of work, every Hadoop-compatible file system should provide location awareness: the name of the rack (more precisely, of the network switch) where a worker node is. Hadoop applications can use this information to run work on the node where the data is, and, failing that, on the same rack/switch, reducing backbone traffic. HDFS uses this method when replicating data to try to keep different copies of the data on different racks. The goal is to reduce the impact of a rack power outage or switch failure, so that even if these events occur, the data may still be readable.

A small Hadoop cluster includes a single master and multiple worker nodes. The master node consists of a JobTracker, TaskTracker, NameNode and DataNode. A slave or worker node acts as both a DataNode and TaskTracker, though it is possible to have data-only worker nodes and compute-only worker nodes. These are normally used only in nonstandard applications. Hadoop requires Java Runtime Environment (JRE) 1.6 or higher. The standard start-up and shutdown scripts require Secure Shell (ssh) to be set up between nodes in the cluster.
In a larger cluster, the HDFS is managed through a dedicated NameNode server to host the file system index, and a secondary NameNode that can generate snapshots of the namenode''s memory structures, thus preventing file-system corruption and reducing loss of data. Similarly, a standalone JobTracker server can manage job scheduling. In clusters where the Hadoop MapReduce engine is deployed against an alternate file system, the NameNode, secondary NameNode and DataNode architecture of HDFS is replaced by the file-system-specific equivalent.

The Hadoop distributed file system (HDFS) is a distributed, scalable, and portable file-system written in Java for the Hadoop framework. Each node in a Hadoop instance typically has a single namenode; a cluster of datanodes form the HDFS cluster. The situation is typical because each node does not require a datanode to be present. Each datanode serves up blocks of data over the network using a block protocol specific to HDFS. The file system uses the TCP/IP layer for communication. Clients use Remote procedure call (RPC) to communicate between each other.
HDFS stores large files across multiple machines. It achieves reliability by replicating the data across multiple hosts, and hence does theoretically not require RAID storage on hosts (but to increase I/O performance some RAID configurations are still useful). With the default replication value, 3, data is stored on three nodes: two on the same rack, and one on a different rack. Data nodes can talk to each other to rebalance data, to move copies around, and to keep the replication of data high. HDFS is not fully POSIX-compliant, because the requirements for a POSIX file-system differ from the target goals for a Hadoop application. The tradeoff of not having a fully POSIX-compliant file-system is increased performance for data throughput and support for non-POSIX operations such as Append.
HDFS added the high-availability capabilities, as announced for release 2.0 in May 2012, allowing the main metadata server (the NameNode) to be failed over manually to a backup in the event of failure. The project has also started developing automatic fail-over.
An advantage of using HDFS is data awareness between the job tracker and task tracker. The job tracker schedules map or reduce jobs to task trackers with an awareness of the data location. For example: if node A contains data (x,y,z) and node B contains data (a,b,c), the job tracker schedules node B to perform map or reduce tasks on (a,b,c) and node A would be scheduled to perform map or reduce tasks on (x,y,z). This reduces the amount of traffic that goes over the network and prevents unnecessary data transfer. When Hadoop is used with other file systems this advantage is not always available. This can have a significant impact on job-completion times, which has been demonstrated when running data-intensive jobs.
File access can be achieved through the native Java API, the Thrift API to generate a client in the language of the users'' choosing (C++, Java, Python, PHP, Ruby, Erlang, Perl, Haskell, C#, Cocoa, Smalltalk, and OCaml), the command-line interface, or browsed through the HDFS-UI webapp over HTTP.
Other file systems[edit]
The fair scheduler was developed by Facebook. The goal of the fair scheduler is to provide fast response times for small jobs and QoS for production jobs. The fair scheduler has three basic concepts.
* Jobs are grouped into Pools.
* Each pool is assigned a guaranteed minimum share.
* Excess capacity is split between jobs.
By default, jobs that are uncategorized go into a default pool. Pools have to specify the minimum number of map slots, reduce slots, and a limit on the number of running jobs.
The capacity scheduler was developed by Yahoo. The capacity scheduler supports several features that are similar to the fair scheduler.
Jobs are submitted into queues.
Queues are allocated a fraction of the total resource capacity.
Free resources are allocated to queues beyond their total capacity.
Within a queue a job with a high level of priority has access to the queue''s resources.
The HDFS file system is not restricted to MapReduce jobs. It can be used for other applications, many of which are under development at Apache. The list includes the HBase database, the Apache Mahout machine learning system, and the Apache Hive Data Warehouse system. Hadoop can in theory be used for any sort of work that is batch-oriented rather than real-time, that is very data-intensive, and able to work on pieces of the data in parallel. As of October 2009, commercial applications of Hadoop included:
Log and/or clickstream analysis of various kinds
Marketing analytics
Machine learning and/or sophisticated data mining
Image processing
Processing of XML messages
Web crawling and/or text processing
General archiving, including of relational/tabular data, e.g. for compliance
Prominent users[edit]

As of 2013, Hadoop adoption is widespread. For example, more than half of the Fortune 50 uses Hadoop.

Hadoop can also be used in compute farms and high-performance computing environments. Instead of setting up a dedicated Hadoop cluster, an existing compute farm can be used if the resource manager of the cluster is aware of the Hadoop jobs, and thus Hadoop jobs can be scheduled like other jobs in the cluster.

Terminology
---
 
* A `Node` is any computational platform that may perform tasks such as computing, storing data, collecting or sending data from/to the internet, and so on.

Fair Distribution
---

Not all computational devices can perform many floating points operations per second, which makes only specific hardware suitable for legacy cryptocurrency mining. HadoopCoin is designed to use all various system resources and not only number crunching, such as data storage, network server, and so on. If the user has a strong CPU or GPU, they can be leveraged as well.

Design considerations:
---

1. All workers will be pure Java (at least on initial releases). Hadoop is best relayed on Java, and Java is of course multi-platform, so even a TV can be a worker.
2. *Jail* technology should be applied, like BSD'' jail. A jail is a mechanism that separates a process (or a user space etc.) from all other machine''s resources, hence exterior computations can be ran on a machine without interefering at all on the user''s work. Jail technologies are considered very secured. It is needed to explore this mechanism in relation to Java.
3. Work should be provable. A worker should be able to prove that it worked, just like cryptocurrency mining. Hence, the type of work that is distributed should be provable only, like Searching, verifying other node''s work, some easily provable mathematical problems (root finding etc.) and so on.
4. Strictly speaking, Hadoop is mainly a huge distributed filesystem (HDFS). So a node can earn HadoopCoins by doing nothing but connecting to the Coordinator''s Hadoop network and serve as a file server.
5. Hadoop takes most care of spreading the work among clients using the famous Map/Reduce approach. In fact, Hadoop and Map/Reduce are almost synonyms.

The general system workflow is as follows:
1. User installs a *Worker* 
