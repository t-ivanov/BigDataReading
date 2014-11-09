Big Data Reading Materials
==============

List of papers, reports and links to materials on Big Data and related topics.

## <a name='TOC'>Table of Contents</a>

  1. [General](#general)
  2. [Block/Page Formats](#page-formats)
  3. [Storage Systems](#storage-systems)
  4. [NoSQL](#nosql)
  5. [Big Data Management Systems](#big-data-man-sys)
  6. [Resource Management](#resource-management)
  7. [Parallel Processing Systems](#processing-systems)
  8. [Hadoop Ecosystem](#hadoop-ecosys)
  9. [SQL-on-Hadoop](#sql-on-hadoop)
  10. [Messaging/Event Systems](#messaging-systems)
  11. [Big Data Benchmarks](#benchmarking)
  12. [External Reading Lists] (#reading-lists)

## <a name='general'> General

* [Toward Scalable Systems for Big Data Analytics A Technology Tutorial] (http://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6842585)
* [The Family of MapReduce and Large Scale Data Processing Systems] (http://arxiv.org/pdf/1302.2966.pdf)
* [Survey of Apache Big Data Stack] (http://grids.ucs.indiana.edu/ptliupages/publications/survey_apache_big_data_stack.pdf)
* [The Beckman Report on Database Research - 2013] (http://beckman.cs.wisc.edu/): Every few years a group of database researchers meets to discuss the state of database research, its impact on practice, and important new directions. This report summarizes the discussion and conclusions of the eighth such meeting, held October 14-15, 2013 in Irvine, California. It observes that Big Data has now become a defining challenge of our time, and that the database research community is uniquely positioned to address it, with enormous opportunities to make transformative impact. To do so, the report recommends significantly more attention to five research areas: scalable big/fast data infrastructures; coping with diversity in the data management landscape; end-to-end processing and understanding of data; cloud services; and managing the diverse roles of people in the data life cycle. 


## <a name='page-formats'> Block/Page Formats


* [(DSM) A decomposition storage model] (http://www3.in.tum.de/teaching/ws0506/MMDBMS/download/decomposition-storage-model.pdf): This report  examines  the relative  advantages of  a storage  model  based  on decomposition  (of community  view  relations  into  binary  relations containing  a surrogate  and  one attribute) over conventional  n-ary  storage  models.

* [(PAX) Weaving Relations for Cache Performance] (http://www.vldb.org/conf/2001/P169.pdf): Relational database systems have traditionally optimzed for I/O performance and organized records sequentially on disk pages using the N-ary Storage Model (NSM) (a.k.a., slotted pages). Recent research, however, indicates that cache utilization and performance is becoming increasingly important on modern platforms. In this paper, we first demonstrate that in-page data placement is the key to high cache performance and that NSM exhibits low cache utilization on modern platforms. Next, we propose a new data organization model called PAX (Partition Attributes Across), that significantly improves cache performance by grouping together all values of each attribute within each page. Because PAX only affects layout inside the pages, it incurs no storage penalty and does not affect I/O behavior. According to our experimental results, when compared to NSM (a) PAX exhibits superior cache and memory bandwidth utilization, saving at least 75% of NSM’s stall time due to data cache accesses, (b) range selection queries and updates on memory-resident relations execute 17-25% faster, and (c) TPC-H queries involving I/O execute 11-48% faster.

* [Column-Stores vs. Row-Stores: How Different Are They Really?] (http://www.cse.iitb.ac.in/dbms/Data/Courses/CS632/2013/Papers/sigmod08-columstore-abadi.pdf)

* [(HPL) A hybrid page layout integrating PAX and NSM] (http://www.hpl.hp.com/techreports/2012/HPL-2012-240.pdf): The present paper explores a hybrid page layout (HPL) that aims to combine the advantages of NSM and PAX. Predicate evaluation in large scan queries have the same number of cache faults as PAX, and space management uses two data areas growing towards each other. Moreover, the design defines a continuum between NSM and PAX in order to support both efficient scans and efficient insertions and updates.
This design is equally applicable to cache lines within RAM memory (the original design goal of PAX) and to small pages on flash storage within large disk pages. Our experimental evaluation is based on an implementation in the former environment. It demonstrates that the HPL design scans almost as fast as the scan-optimized PAX layout and updates almost as fast as the update-optimized NSM layout, i.e., it is competitive with both in their best use cases. 

* [Column-Oriented Storage Techniques for MapReduce] (http://arxiv.org/ftp/arxiv/papers/1105/1105.4252.pdf)

* [Trojan Data Layouts: Right Shoes for a Running Elephant] (https://infosys.uni-saarland.de/publications/JQD11.pdf)

* [Dremel: Interactive Analysis of Web-Scale Datasets] (http://ftp.cs.duke.edu/courses/cps296.4/compsci590.4/fall13/838-CloudPapers/Dremel.pdf) & [Parquet] (http://parquet.incubator.apache.org/): Apache Parquet is a columnar storage format available to any project in the Hadoop ecosystem, regardless of the choice of data processing framework, data model or programming language.

* [RCFile: A Fast and Space-efficient Data Placement Structure in MapReduce-based Warehouse Systems] (http://web.cse.ohio-state.edu/hpcs/WWW/HTML/publications/papers/TR-11-4.pdf): MapReduce-based data warehouse systems are playing important roles of supporting big data analytics to understand quickly the dynamics of user behavior trends and their needs in typical Web service providers and social network sites
(e.g., Facebook). In such a system, the data placement structure is a critical factor that can affect the warehouse performance in a fundamental way. Based on our observations and analysis of Facebook production systems, we have characterized four requirements for the data placement structure: (1) fast data loading, (2) fast query processing, (3) highly efficient storage space utilization, and (4) strong adaptivity to highly dynamic workload patterns. We have examined three commonly accepted data placement structures in conventional databases, namely row-stores,column-stores, and hybrid-stores in the context of large data analysis using MapReduce. We show that they are not very suitable for big data processing in distributed systems. In this paper, we present a big data placement structure called RCFile
(Record Columnar File) and its implementation in the Hadoop system. With intensive experiments, we show the effectiveness of RCFile in satisfying the four requirements. RCFile has been chosen in Facebook data warehouse system as the default option. It has also been adopted by Hive and Pig, the two most widely used data analysis systems developed in Facebook and Yahoo!

* [(ORC File) Major Technical Advancements in Apache Hive] (http://web.cse.ohio-state.edu/hpcs/WWW/HTML/publications/papers/TR-14-2.pdf)



## <a name='storage-systems'> Storage Systems

* [The Google File System](http://research.google.com/archive/gfs.html) (2003) & [Bigtable: A Distributed Storage System for Structured Data](http://research.google.com/archive/bigtable.html) (2006): Two core components of Google's data infrastructure. GFS is an append-only distributed file system for large sequential reads (data-intensive applications). BigTable is high-performance distributed data store that builds on GFS. One way to think about it is that GFS is optimized for high throughput, and BigTable explains how to build a low-latency data store on top of GFS. Some of these might have been replaced by newer proprietary technologies internal to Google, but the ideas stand.

* [HDFS Architecture Guide] (http://pristinespringsangus.com/hadoop/docs/hdfs_design.pdf) & [The hadoop distributed file system] (The hadoop distributed file system): The Hadoop Distributed File System (HDFS) is designed to store very large data sets reliably, and to stream those data sets at high bandwidth to user applications. In a large cluster, thousands of servers both host directly attached storage and execute user application tasks. By distributing storage and computation across many servers, the resource can grow with demand while remaining economical at every size. We describe the architecture of HDFS and report on experience using HDFS to manage 25 petabytes of enterprise data at Yahoo!.

* [C-Store: A Column-oriented DBMS](http://www.cs.berkeley.edu/~rxin/db-papers/C-Store.pdf) (2005) & [The Vertica Analytic Database: C-Store 7 Years Later](http://vldb.org/pvldb/vol5/p1790_andrewlamb_vldb2012.pdf) (2012): C-Store is an influential, academic system done by the folks in New England. Vertica is the commercial incarnation of C-Store. 

* [Tachyon: Reliable, Memory Speed Storage for Cluster Computing Frameworks] (http://www.cs.berkeley.edu/~haoyuan/papers/2014_socc_tachyon.pdf) & [Tachyon: Memory Throughput I/O for Cluster Computing Frameworks] (http://www.eecs.berkeley.edu/~alig/papers/tachyon-workshop.pdf): Tachyon is a distributed file system enabling reliable data sharing at memory speed across cluster computing frameworks. While caching today improves read workloads, writes are either network or disk bound, as replication is
used for fault-tolerance. Tachyon eliminates this bottleneck by pushing lineage, a well-known technique, into the storage layer. The key challenge in making a long-running lineage-based storage system is timely data recovery in case of failures. Tachyon addresses this issue by introducing a checkpointing algorithm that guarantees bounded recovery cost and resource allocation strategies for recomputation under commonly used resource schedulers. Our evaluation shows that Tachyon outperforms in-memory HDFS by 110x for writes. It also improves the end-to-end latency of a realistic workflow by 4x. Tachyon is open source and is deployed at multiple companies.

## <a name='nosql'> NoSQL

* [(basics) NoSQL Databases] (http://www.christof-strauch.de/nosqldbs.pdf)
* [Bigtable: A Distributed Storage System for Structured Data] (http://www3.in.tum.de/teaching/ss10/WebDatabases/bigtable-osdi06.pdf)

* [Chord: A Scalable Peer-to-peer Lookup Service for Internet Applications](http://www.cs.berkeley.edu/~rxin/db-papers/Chord-DHT.pdf) (2001) & [Dynamo: Amazon’s Highly Available Key-value Store](http://www.cs.berkeley.edu/~rxin/db-papers/Dynamo.pdf) (2007): Chord was born in the days when distributed hash tables was a hot research. It does one thing, and does it really well: how to look up the location of a key in a completely distributed setting (peer-to-peer) using consistent hashing. The Dynamo paper explains how to build a distributed key-value store using Chord. Note some design decisions change from Chord to Dynamo, e.g. finger table O(logN) vs O(N), because in Dynamo's case, Amazon has more control over nodes in a data center, while Chord assumes peer-to-peer nodes in wide area networks.

* [Cassandra-A Decentralized Structured Storage System] (http://www.cs.ucr.edu/~tsotras/cs260/F12/cassandra.pdf): Cassandra is a distributed storage system for managing very large amounts of structured data spread out across many
commodity servers, while providing highly available service with no single point of failure. Cassandra aims to run on top of an infrastructure of hundreds of nodes (possibly spread across different data centers). At this scale, small and large components fail continuously. The way Cassandra manages the persistent state in the face of these failures drives the reliability and scalability of the software systems relying on this service. While in many ways Cassandra resembles a database and shares many design and implementation strategies therewith, Cassandra does not support a full relational data model; instead, it provides clients with a simple data model that supports dynamic control over data layout and format. Cassandra system was designed to run on cheap commodity hardware and handle high write throughput while not sacriffcing read effciency.

* [(book) Cassandra: The Definitive Guide] (http://filepi.com/i/R1Cuxhb)

## <a name='big-data-man-sys'> Big Data Management Systems

* [Spanner](http://static.googleusercontent.com/media/research.google.com/en//archive/spanner-osdi2012.pdf) (2012): Spanner is "a scalable, multi-version, globally distributed, and synchronously replicated database". The linchpin that allows all this functionality is the TrueTime API which lets Spanner order events between nodes without having them communicate. [There is some speculation that the TrueTime API is very similar to a vector clock but each node has to store less data](http://www.cse.buffalo.edu/~demirbas/publications/augmentedTime.pdf). Sadly, a paper on TrueTime is promised, but hasn't yet been released.

* [AsterixDB: A Scalable, Open Source BDMS] (http://www.vldb.org/pvldb/vol7/p1905-alsubaiee.pdf) (2014): AsterixDB is a new, full-function BDMS (Big Data Management System) with a feature set that distinguishes it from other platforms in today’s open source Big Data ecosystem. Its features make it well-suited to applications like web data warehousing, social data storage and analysis, and other use cases related to Big Data. AsterixDB has a flexible NoSQL style data model; a query language that supports a wide range of queries; a scalable runtime; partitioned, LSM-based data storage and indexing (including B+ -tree, R-tree, and text indexes); support for external as well as natively stored
data; a rich set of built-in types; support for fuzzy, spatial, and temporal types and queries; a built-in notion of data feeds for ingestion of data; and transaction support akin to that of a NoSQL store.

* [Mesa: Geo-Replicated, Near Real-Time, Scalable Data Warehousing] (http://www.vldb.org/pvldb/vol7/p1259-gupta.pdf) (2014): Mesa is a highly scalable analytic data warehousing system that stores critical measurement data related to Google’s Internet advertising business. Mesa is designed to satisfy a complex and challenging set of user and systems requirements, including near real-time data ingestion and queryability, as well as high availability, reliability, fault tolerance,and scalability for large data and query volumes. Specifically, Mesa handles petabytes of data, processes millions of row updates per second, and serves billions of queries that fetch trillions of rows per day. Mesa is geo-replicated across multiple datacenters and provides consistent and repeatable query answers at low latency, even when an entire datacenter fails. This paper presents the Mesa system and reports the performance and scale that it achieves.

* [DataHub: Collaborative Data Science & Dataset Version Management at Scale] (http://arxiv.org/abs/1409.0798) (2014): Dataset Version Control System (DSVC), is a system for multi-version dataset management. DSVC’s goal is to provide a common substrate to enable data scientists to capture their modifications, minimize storage costs, use a declarative language to reason about versions, identify differences between versions, and share datasets with other scientists. Second, DATAHUB, is a hosted platform built on top of DSVC, that not only supports richer interaction capabilities, but also provides a number of novel tools for data cleaning, data search and integration, and data visualization tools. 

## <a name='resource-management'> Resource Management

* [The Datacenter Needs an Operating System] (https://www.usenix.org/legacy/event/hotcloud11/tech/final_files/Zaharia.pdf)

* [Mesos: A Platform for Fine-Grained Resource Sharing in the Data Center] (http://static.usenix.org/events/nsdi11/tech/full_papers/Hindman_new.pdf) & [Apache Mesos] (http://mesos.apache.org/): We present Mesos, a platform for sharing commodity clusters between multiple diverse cluster computing frameworks, such as Hadoop and MPI. Sharing improves cluster utilization and avoids per-framework data replication. Mesos shares resources in a fine-grained manner, allowing frameworks to achieve data locality by taking turns reading data stored on each machine. To support the sophisticated schedulers of today’s frameworks, Mesos introduces a distributed two-level scheduling mechanism called resource offers. Mesos decides how many resources to offer each framework, while frameworks decide which resources to accept and which computations to run on them. Our results show that Mesos can achieve near-optimal data locality when sharing the cluster among diverse frameworks, can scale to 50,000 (emulated) nodes, and is resilient to failures.

* [Omega: flexible, scalable schedulers for large compute clusters] (http://static.googleusercontent.com/media/research.google.com/en//pubs/archive/41684.pdf): Increasing scale and the need for rapid response to changing requirements are hard to meet with current monolithic cluster scheduler architectures. This restricts the rate at which new features can be deployed, decreases efficiency and utilization, and will eventually limit cluster growth. We present a novel approach to address these needs using parallelism, shared state, and lock-free optimistic concurrency control. We compare this approach to existing cluster scheduler designs, evaluate how much interference between schedulers occurs and how much it matters in practice, present some techniques to alleviate it, and finally discuss a use case highlighting the advantages of our approach – all driven by real-life Google production workloads.
 
* [Apache Hadoop YARN: yet another resource negotiator] (https://54e57bc8-a-62cb3a1a-s-sites.googlegroups.com/site/2013socc/home/program/a5-vavilapalli.pdf?attachauth=ANoY7crrl3LueZKiJV4CAYJgK2jv4N8iE2Asqa9wwGeKUwhQVSmfDnvX9Iqb6cNQth2DtlMG99O5hJTOTkJkCUl0r6txC3JVaumyuAe977DaELZufXYPul83aJRSdIt_fotZMNspdOQjdqIfJ4Vb6Yktw_i5sAcY1GySSIJUaY3VLLIu2h7N8lqgPf484j-DgvLiICXVg5GdqjytjtqLcP8DuLSOiOZOMzDhYdObvvI_9KZa9WUoJIY%3D&attredirects=0) (2013): The initial design of Apache Hadoop [1] was tightly focused on running massive, MapReduce jobs to process a web crawl. For increasingly diverse companies, Hadoop has become the data and computational agora — the de facto place where data and computational resources are shared and accessed. This broad adoption and ubiquitous
usage has stretched the initial design well beyond its intended target, exposing two key shortcomings: 1) tight coupling of a specific programming model with the resource management infrastructure, forcing developers to abuse the MapReduce programming model, and 2) centralized handling of jobs’ control flow, which resulted in endless scalability concerns for the scheduler. In this paper, we summarize the design, development,and current state of deployment of the next generation of Hadoop’s compute platform: YARN. The new architecture we introduced decouples the programming model from the resource management infrastructure, and delegates many scheduling functions (e.g., task fault-tolerance) to per-application components. We provide experimental evidence demonstrating the improvements we made, confirm improved efficiency by reporting the experience of running YARN on production environments (including 100% of Yahoo! grids), and confirm the flexibility claims by discussing the porting of several programming frameworks onto YARN viz. Dryad, Giraph, Hoya, Hadoop MapReduce, REEF, Spark, Storm, Tez.

## <a name='processing-systems'> Parallel Processing Systems

* [MapReduce: Simplified Data Processing on Large Clusters](http://research.google.com/archive/mapreduce.html) (2004): MapReduce is both a programming model (borrowed from an old concept in functional programming) and a system at Google for distributed data-intensive computation. The programming model is so simple yet expressive enough to capture a wide range of programming needs. The system, coupled with the model, is fault-tolerant and scalable. It is probably fair to say that half of the academia are now working on problems heavily influenced by MapReduce.

* [Dryad: Distributed Data-Parallel Programs from Sequential Building Blocks] (http://cs.brown.edu/~debrabant/cis570-website/papers/dryad.pdf) (2007): Dryad is a programming model developed at Microsoft that enables large scale dataflow programming. "The fundamental difference between the \[MapReduce and Dryad\] is that a Dryad application may specify an arbitrary communication DAG rather than requiring a sequence of map/distribute/sort/reduce operations". 

* [Spark: cluster computing with working sets] (http://static.usenix.org/legacy/events/hotcloud10/tech/full_papers/Zaharia.pdf): MapReduce and its variants have been highly successful in implementing large-scale data-intensive applications on commodity clusters. However, most of these systems are built around an acyclic data flow model that is not suitable for other popular applications. This paper focuses on one such class of applications: those that reuse a working set of data across multiple parallel operations. This includes many iterative machine learning algorithms, as well as interactive data analysis tools. We propose a new framework called Spark that supports these applications while retaining the scalability and fault tolerance of MapReduce. To achieve these goals, Spark introduces an abstraction called resilient distributed datasets (RDDs). An RDD is a read-only collection of objects partitioned across a set of machines that can be rebuilt if a partition is lost. Spark can outperform Hadoop by 10x in iterative machine learning jobs, and can be used to interactively query a 39 GB dataset with sub-second response time.

* [Resilient distributed datasets: A fault-tolerant abstraction for in-memory cluster computing] (https://www.usenix.org/system/files/conference/nsdi12/nsdi12-final138.pdf): We present Resilient Distributed Datasets (RDDs), a distributed memory abstraction that lets programmers perform in-memory computations on large clusters in a fault-tolerant manner. RDDs are motivated by two types of applications that current computing frameworks handle inefficiently: iterative algorithms and interactive data mining tools. In both cases, keeping data in memory can improve performance by an order of magnitude. To achieve fault tolerance efficiently, RDDs provide a restricted form of shared memory, based on coarse-grained transformations rather than fine-grained updates to shared state. However, we show that RDDs are expressive enough to capture a wide class of computations, including recent specialized programming models for iterative jobs, such as Pregel, and new applications that these models do not capture. We have implemented RDDs in a system called Spark, which we evaluate through a variety of user applications and benchmarks.

* [(PhD Thesis Zaharia) An Architecture for Fast and General Data Processing on Large Clusters] (http://www.eecs.berkeley.edu/Pubs/TechRpts/2014/EECS-2014-12.pdf)

## <a name='hadoop-ecosys'> Hadoop Ecosystem

* [(book) Hadoop Operations - A Guide for Developers and Administrators] (http://filepi.com/i/tsRd73q)
* [(book) Hadoop: The Definitive Guide, 3rd Edition] (http://filepi.com/i/8hYSHSh)

## <a name='sql-on-hadoop'> SQL-on-Hadoop

* [Shark: SQL and Rich Analytics at Scale](https://amplab.cs.berkeley.edu/publication/shark-sql-and-rich-analytics-at-scale/) (2013): Describes the Shark system, which is the SQL engine built on top of Spark. More importantly, the paper discusses why previous SQL on Hadoop/MapReduce query engines were slow.



## <a name='messaging-systems'> Messaging/Event Systems

* [Kafka: a Distributed Messaging System for Log Processing] (http://research.microsoft.com/en-us/UM/people/srikanth/netdb11/netdb11papers/netdb11-final12.pdf): Log processing has become a critical component of the data pipeline for consumer internet companies. We introduce Kafka, a distributed messaging system that we developed for collecting and delivering high volumes of log data with low latency. Our system incorporates ideas from existing log aggregators and messaging systems, and is suitable for both offline and online message consumption. We made quite a few unconventional yet practical design choices in Kafka to make our system efficient and scalable. Our experimental results show that Kafka has superi or performance when compared to two popular messaging systems. We have been using Kafka in production for some time and it is processing hundreds of gigabytes of new data each day.

* [The big data ecosystem at LinkedIn] (http://dl.acm.org/citation.cfm?id=2463707)

* [Storm @ Twitter - Nathan Marz] (http://assets.en.oreilly.com/1/event/75/Storm_%20distributed%20and%20fault-tolerant%20realtime%20computation%20Presentation.pdf) 

* [Storm @ Twitter - paper] (http://dl.acm.org/citation.cfm?id=2595641)

* [SAMOA: a platform for mining big data streams] (http://dl.acm.org/citation.cfm?id=2488042)

## <a name='benchmarking'> Big Data Benchmarks

* [The HiBench benchmark suite: Characterization of the MapReduce-based data analysis] (https://github.com/intel-hadoop/HiBench/blob/8a8fba75a1055c5f72b0834f13e66275ca788a76/WISS10_conf_full_011.pdf) &  [HiBench: A Representative and Comprehensive Hadoop Benchmark Suite] (http://clds.sdsc.edu/sites/clds.sdsc.edu/files/wbdb2012/papers/WBDB2012Paper38Gowda.pdf)

* [Bigdatabench: A big data benchmark suite from internet services] (http://arxiv.org/abs/1401.1406)

* [Bigbench: Towards an industry standard benchmark for big data analytics] (http://grail.csuohio.edu/~sschung/cis611/BigBenchmarkSig2014-ghazal.pdf) & [BigBench Specification V0. 1] (http://www.msrg.org/publications/pdf_files/2013/RablWBDB22013-BigBench_Specification_V0.1.pdf)
* [A BigBench Implementation in the Hadoop Ecosystem] ()
* [Discussion of BigBench:A Proposed Industry Standard Performance Benchmark for Big Data] (http://www.msrg.org/publications/pdf_files/2014/TPCTC2014-Rabl-Discussion_of_BigBench:_A_Prop.pdf)

## <a name='reading-lists'> External Reading Lists

* [Readings in Databases] (https://github.com/rxin/db-readings)

