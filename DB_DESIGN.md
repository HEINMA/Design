# DB requiremnt.
In health care industry lot of informations are updated regularly. To make system are not absoleete with the time , those are needed to capable to add defferent ifnormtions and data to database simply.
But sql databases are basically relation oriented. It is required regid database architecture. 

These Informations about no-sql databases are taken from following url and you can register and access scylladb white papers regarding nosql database.

https://lp.scylladb.com/sql-to-nosql-architecture-wp-thanks.html

Today, the most iconic and familiar
relational databases include IBM DB2, Oracle
Database, Microsoft SQL Server, PostgreSQL,
and MySQL.

Structured Query Language, or SQL, was
invented at IBM soon after the introduction of
the relational database. Since its introduction,
SQL has become the most widely used
database language, used for querying data, data
manipulation (insert, update and delete), data
definition (schema creation and modification),
and data access control.

Times have changed. The advent of
smartphones, the ‘app economy,’ and cloud
computing in the late 2000s caused a seachange
in the workloads, query types, and traffic
patterns needed to support a global user base.

Latency issues can be addressed by shifting
data closer to the customer. To meet this
need, data must be replicated across different
geographic locations. Such geographical
replication turned out to be a struggle for
RDBMSs. While RDBMSs are not fit for
distributed deployments, non-relational
databases are designed specifically to support
such topologies

A number of alternative non-relational database
systems have been proposed, including Google’s
Bigtable (2006) and Amazon’s Dynamo (2007).
The papers for these projects paved the way
for Cassandra (2008) and MongoDB (2009).

![no sql comparison](images/nosql_1.png?raw=true "https://scylladb.drift.click/wp-sql-nosql")

## ECONOMIES OF SCALE

1. Database administrators add capacity to RDBMS
and NoSQL databases in very different ways.
2. Typically, the only way to add capacity in a
relational system is to add expensive hardware,
faster CPUs, more RAM, and more advanced
networking components. 
3. This is often referred to
as ‘vertical’ scale, or ‘scaling up.’

4. In contrast, NoSQL databases are designed
for low latency and high resilience, being built
from the ground up to run across clusters of
distributed nodes. 
5. This architecture is often
referred to as ‘horizontal scale,’ or ‘scaling
out.’ To add capacity to a NoSQL database,
administrators simply add more nodes, a very
simple process in modern cloud environments.

6. In a NoSQL cluster, nodes are easy to add and
remove according to demand, providing ‘elastic’
capacity. This feature enables organizations
to align their data footprint with the needs of
the business while maintaining availability even
in the face of seasonal demand spikes, node
failures, and network outages.

7. The horizontal scale of NoSQL brings tradeoffs
of its own. Adding commodity hardware to
a cluster can be cheap in terms of software
licenses and subscriptions. However, as more
and more nodes are added in the pursuit of
higher throughput and lower latency, operational
overhead and administrative costs spike. Big
clusters of small instances demand more
attention and generate more alerts than small
clusters of large instances.

## REPLICAS OF DATA
Replicating data across multiple nodes allows
databases to achieve higher levels of resilience.
In the RDBMS world, it’s not trivial to replicate
data across multiple instances. Relational
databases do not support replication. Instead,
they rely on external tools to extract and update
copies of datasets. These tools run batch
processes that often take hours to complete.
As a result, there is no way to ensure real-time
synchronization of data among the copies of
data.

While non-relational databases provide native
support for data replication, they follow three
basic models: 
### multi-master databases, such as
DynamoDB, 
### master-slave architectures, such as
MongoDB, and 
## masterless, such as Scylla. 

Given their reliance on master nodes, both multi-
master and master-slave architecture introduce
a point of failure. When a master goes down, the
process of electing a new master introduces a
brief downtime. Even though the delay may be
minimal, measured in milliseconds, that delay
can still cause SLA violations.

In a masterless architecture, no single node
can bring down an entire cluster. A typical
masterless topology involves three or more
replicas for each dataset. Adopting a NoSQL
database that implements a masterless
architecture provides yet another layer
of resilience for high-volume, low-latency
applications.


## APPLICATION-DRIVEN USE CASES
The rise in popularity of NoSQL databases
paralleled the adoption of agile development
and DevOps practices. Unlike RDBMSs, NoSQL
databases encourage ‘application-first’ or
API-first development patterns. Following
these models, developers first consider queries
that support the functionality specific to an
application, rather than considering the data
models and entities. This developer-friendly
architecture paved the path to the success of
the first generation of NoSQL databases.

In contrast, relational databases impose fairly
rigid, schema-based structures to data models;
tables consisting of columns and rows, which
can be joined to enable ‘relations’ among
entities. Each table typically defines an entity.
Each row in a table holds one entry, and each
column contains a specific piece of information
for that record. The relationships among tables
are clearly defined and usually enforced by
schemas and database rules.

Relational data models enforce uniformity,
whereas non-relational models do not. NoSQL
databases permit multiple ‘shapes’ of data
objects to coexist, which is more flexible but
can also be more error prone. In the world
of relational databases, the schemas that
support uniformity are usually managed by
database administrators. This can sometimes
introduce friction between administrators and
development teams, resulting in long, non-agile
application development lifecycles. Such highly
structured data requires normalization to reduce
redundancy. Since the data model is based on
the entity being represented; query patterns are
a secondary consideration.

NoSQL inverts this approach, placing more
power in the hands of the developer and often
decentralizing control over data structures. Non-
relational data models are flexible, and schema
management is often delegated to application
developers, who are relatively free to adapt data
models independently. Such a decentralized
approach can accelerate development
cycles and provide a more agile approach to
addressing user requirements.

## CONSISTENCY VERSUS AVAILABILITY
A consideration of the architectural differences
between relational and non-relational databases
would not be complete without the CAP
theorem. The CAP theorem was formulated by
Eric Brewer in 2000, as a way of expressing
the key tradeoffs in distributed systems. The
CAP theorem states that it is impossible for a
distributed data store to provide more than two
of the following three guarantees:

* Consistency: Every read receives either the
most recent write or an error.
* Availability: Every request receives a response
that is not an error, but with no guarantee that
it contains the most recent write.
* Partition Tolerance: The system continues to
operate even when an arbitrary number of
messages are delayed, dropped or reordered
among nodes.

Another way of putting this is that the CAP
theorem dictates that any data store brings
with it a fundamental trade-off. As such, many
databases are referred to as CP (consistent
and partition tolerance, but not available)
or AP (available and partition-tolerant, but
not consistent). In CAP terms, the critical
trade-off that distinguishes relational and non-
relational data stores is between availability and
consistency. SQL data stores sacrifice availability
in favor of data consistency. NoSQL data stores
sacrifice consistency in favor of availability.

It is important to note that the CAP theorem
has come under significant criticism. Martin
Kleppmann, in particular, has written a
comprehensive Critique of the CAP Theorem.
So, it is important to keep in mind that the
theorem is merely a simplified model for
understanding a very complex topic.


## ACID VERSUS BASE CONSISTENCY
One of the defining tradeoffs between relational
and non-relational datastores is in the type
of consistency that they provide. In simple
terms, RDBMS provides strong consistency,
while NoSQL databases provide a weaker form.
Consistency in general refers to a database’s
ability to process concurrent transactions while
preserving the integrity of the data. Somewhat
confusingly, ‘consistency’ as defined in the
CAP theorem has a different, though related,
meaning than the consistency discussed in this
section. The definition used by Brewer in the
CAP theorem derives from distributed systems
theory, while the definition used in this section
derives from database theory.

7
In simple terms, consistency is a guarantee that
a read should return the result of the latest
successful write. This seems simple, but such
a guarantee is incredibly difficult to deliver
without impacting the performance of the
system as a whole. In a relational database,
a single data item is actually split across
independent registers that must agree with one
another. Thus, a single database write is actually
decomposed into several small writes to these
registers, which must be completed and visible
when the read is executed. With concurrent
operations running against the database, the
semblance of order between the group of
sub-operations needs to be maintained; the
concurrent operations must be atomic. ACID
consistency means the rules of relations must
be satisfied. In a globally distributed database
topology, which involves multiple clusters
each containing many nodes the problem
of consistency becomes exponentially more
complex.

ACID is more descrivbed in the white paper but not to be abbrivated hear.

By their nature, ACID-compliant databases are
generally slow, difficult to scale, and expensive
to run and maintain. It should be noted some
RDBMS systems enable performance to be
improved by relaxing ACID guarantees. Still,
all SQL databases are ACID compliant to
varying degrees, and as such, they all share
this downside. The practical effect of ACID
compliance is to make it extraordinarily difficult
and expensive to achieve resilient, distributed
SQL database deployments.

In contrast to RDBMS’ ACID guarantees, NoSQL
databases provide so-called ‘BASE guarantees.’
BASE enables availability and relaxes the
stringent consistency. The acronym BASE
designates:
*  Basic Availability: Data is available most of
the time, even during a partial system failure.
*  Soft state: Individual data items are
independent and do not have to be consistent
with each other.
*  Eventual consistency: Data will become
consistent at some unspecified point in the
future.

As such, NoSQL databases sacrifice a degree
of consistency in order to increase availability.
Rather than providing strong consistency,
NoSQL databases generally provide eventual
consistency. A data store that provides
BASE guarantees can occasionally fail to
return the result of the latest write, providing
different answers to applications making
requests. Developers building applications
against eventually consistent data stores
often implement consistency checks in their
application code.

## Lightweight transactions
In a traditional SQL RDBMS, a “transaction”
is a logical unit of work — a group of tasks
that provides the ACID guarantees discussed
above. To compensate for relaxed consistency,
some NoSQL databases offer ‘lightweight
transactions’ (LWTs).
Lightweight transactions are limited to a single
conditional statement, which enables an atomic
“compare and set” operation. Such an operation
checks whether a condition is true before it
conducts the transaction. If the condition is not
met, the transaction is not executed. (For this
reason, LWTs are sometimes called ‘conditional
statements’). LWTs do not truly lock the
database for the duration of the transaction;
they only ‘lock’ a single cell or row. LWTs
leverage a consensus protocol such as Paxos
to ensure that all nodes in the cluster agree
the change is committed. In this way, LWTs can
provide sufficient consistency for applications
that require the availability and resilience of a
distributed database.


## QUERY LANGUAGES: SQL VERSUS CQL
As we’ve noted, relational databases are defined
in part by their use of the Structured Query
Language (SQL). In contrast, NoSQL databases
employ a host of alternative query languages
that have been designed to support diverse
application use cases. A partial list includes
MongoDB Query Language (MQL), Couchbase’s
N1QL, Elasticsearch’s Query DSL, Microsoft
Azure’s Cosmos DB query language, and
Cassandra Query Language (CQL).

## Limitations in CQL
SQL and CQL share similar statements to store
and modify data, such as Create, Alter, Drop, and
Truncate commands, but unlike SQL, CQL is not
designed to support joins between tables. In CQL,
relations are implemented within the application,
rather than within the database query.

## Values versus objects
Query results are also returned differently. SQL
natively returns data-typed values, usually to
be read into an object one field at a time. In
contrast, CQL natively returns complete objects,
often serialized in extensible markup language
(XML) or Javascript object notation (JSON). This
makes applications responsible for parsing these
objects to obtain the desired result of a query.


## Scaling characteristics
In NoSQL, data is stored across nodes in a
cluster based on a token range, which is a
hashed value of the primary key. By using token
ranges, NoSQL databases enable objects to
be stored on different nodes. CQL queries are
inherently more scalable than SQL queries,
having been specifically designed to query
across a horizontally distributed cluster of
servers, rather than a single database at a time.

When migrating from SQL to NoSQL, the
primary key in the relational table becomes the
partition key in the NoSQL table. If the RDBMS
table must be joined to additional tables to
retrieve the business object, those closely
related tables should combine into a single
NoSQL table. The NoSQL cluster ordering key
determines the physical order of records, so it
should be a unique value (often a composite
value) that would be useful for searching



![no sql partition](images/no-sql-02.png?raw=true "https://scylladb.drift.click/wp-sql-nosql")

## QUERY PATTERNS
Relational databases are organized around data
structures and relationships. In contrast, NoSQL
databases are organized around query patterns.
As noted above, the NoSQL partition key can
be mapped to a primary key in an RDBMS.

Secondary keys and indexes can be added
later. A UNIQUE constraint in a SQL database
becomes a good candidate for a cluster
ordering key in NoSQL.


Scylladb white paper discuss more about no sql database migration from sql to no sql and node repaire etc.

But according to HEINMA requirement we need to avoide being absoleete our system over the time due to change of information. So we have decided to go for nosql database. Even now we have pioratized the consistancy over availability due to this is a health information management system. 

It was considered the popularity of the solution, being a open source solution and the available free supoort for the development. So Mongo DB and Apache Cassendra was amoong final two selections.

Comparison between MongoDB and casendra is as follows.

https://www.knowledgehut.com/blog/data-science/cassandra-vs-mongodb







