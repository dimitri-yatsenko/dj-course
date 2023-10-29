# Why Databases

```{image} ../images/shop.png
:alt: scientific workflow
:class: bg-primary mb-1
:width: 600px
:align: center
```

## When should you use a database and why?


The word *database* is often used rather loosely to describe any *data collection*  or *data repository*.
For the purposes of this book we will use a more specific definition:

```{card} 
 A **database** is a time-varying  collection of structured data serving as an integral part of a real-world enterprise, supporting its operations and accessed in various ways by diverse participants. 
```

Hotels and airlines, stores, hospitals, universities,  banks, and research projects commonly rely on databases for their orderly operations.
The database tracks the current state of the overall process and enforces the essential *business rules*, facilitating valid transactions and preventing illegal or invalid operations or anomalous states. 

Then a **database management system** is a computing system that enables defining and enforcing the data structure and the logic for specified business rules.
Database management systems handle data storage and execute data manipulations and queries efficiently while enforcing the structure and  maintaining the integrity of the data under the stresses of such concurrent manipulations.

For example, an airline may rely on a database for scheduling flights and booking tickets.
The airline needs to enforce many business rules such as:

* a seat on a flight cannot have two outstanding reservation,
* a reservation can be made only when required information is completed and verified and the payment has been confirmed,
* a reservation may be cancelled 24 hours before the flight.

A good database management system would provide rich constructs for expressing and enforcing these types of constraints.

The state of the data may evolve quickly through concurrent interactions with many agents: both human users and various digital processes.
Disruptions such as power and network outages should result in no lasting anomalies, restoring the overall system to a valid state,
To each agent, the database must appear available and responsive as if no one else mattered, quickly integrating each action without blocking or colliding with the actions of others.  

Is the above definition too narrow?

After all, someone might build a database for much less demanding scenarios such as organizing a personal collection of cooking recipes or an address book for personal use.
The above definition targets the functions and scenarios that only full-featured database systems can adequately support and where other approaches *e.g.* shared file repositories) will likely fail. 
Managing a personal recipe collection can be done in Google Drive nearly as well as in a relational database.
However, running a bank, an airline, or a stock exchange will require an advanced database system.

The Aristotelian *telos* of databases is to support mission-critical operations of data-driven enterprises with many diverse and dispersed participants.

## Data queries
*Data repositories*, which are a broader category of data management systems, generally allow depositing and retrieving data.

```{card} 
**Data retrieval** delivers data from a *data repository* in the same form as deposited.
```

In contrast, databases commonly support diverse user segments with different roles and interests in the operations of their enterprise.
To meet their needs, databases must support \emph{data queries}: requests for specific cross-section of the store data in a desired form, often quite different from the form in which the data is stored. 


```{card}
**A data query** is a function on the stored data capable of deriving and delivering a specified cross-section of the data in the database as necessary for the specific analysis---often quite different from the form in which the data are stored.
Database systems provide rich tools for defining and executing precise queries.
```

For example, university students need to register for courses and to view their transcripts whereas course instructors need to view the course rosters and to enter grades for their students while the dean may need to see the grades of all the students in her department. 
All these queries produce results derived from the same stored data through selecting and aggregating specific items across the dataset.

In modern data-centric scientific studies, data queries are especially helpful for selecting and aggregating the specific pieces of data needed for a particular analysis or visualization without having to download the entire dataset from the repository where it's collected.

## Data structure and integrity
Databases can provide a way to express and enforce the structure of the data and the business rules.


If the database must represent processes in the real world accurately and precisely and to enforce business rules while interacting concurrently with many agents, it must provide strong measures to prevent corruption.
Corruption may include invalid or incomplete data entry, data loss, alteration, misidentification, mismatch, duplication, loss of references.
   
Section  describes the three from of data integrity in DataJoint:
* domain integrity
* completeness 
* entity integrity
* referential integrity
* compositional integrity

## Data Consistency
To effectively represent the current state of the enterprise, the database must present the same data to all participants simultaneously and integrate their concurrent inputs. In other words, the database must ensure \emph{data consistency}.

```{card}
**Data consistency** is the ability of a database to maintain the appearance of a single valid current copy of the data to all participants even as they access and change the data concurrently.
Any successful query (read) must reflect the most recent state of the database.
Any successful write must have immediate and durable effect on all subsequent reads.
```

Data consistency is best illustrated by cases when it's violated.
For example, I noticed that around 4 o'clock in the morning my bank's  website already shows the pending transactions from the previous day without reflecting them in the checking account balance.
By 5.30 a.m. the account balance gets updated too.
This is an example of data inconsistency: the view of account transactions reflects a different state than the view of the account balance.
I am confident that the data inconsistency in this case is limited to the web application since I have never observed any unreconciled account balances: the website always catches up to a consistent state.

In many scenarios maintaining data consistency is rather trivial.
The easiest way to ensure data consistency is to avoid conditions that can lead to it.
For example, if only one participant produces the data and all others only consume it, then there is little chance for conflicts and tensions that can lead to inconsistency.
Even delayed queries reflect a consistent state from an earlier time.
These types of scenarios are common in science projects: a single lab produces the data and ensures its consistency while other groups only consume the data.


Far more complex scenarios arise when multiple participants, human or virtual, need to access and alter the data concurrently.
Integrating their activities with minimum delay and without introducing inconsistencies becomes much more challenging.
To preserve consistency, the system may temporarily restrict access for some participants while another completes her transaction.
Or the system may force participants to resolve conflicts before merging the data.

```{card}
ACID model for database transactions:
* **A**tomic
* **C**onsistent
* **I**solated
* **D**urable
```

Relational databases provide a strong consistency model called ACID where data operations are ensured to be atomic, consistent, isolated, and durable.

When the participants are physically dispersed and the data storage must be distributed to make the data more readily available with slow or intermittent network connectivity, then ensuring data consistency becomes particularly challenging.
In fact, for a long time it was believed that  data systems distributed across large geographical spans were incompatible with data consistency:
One particular result, the so-called **CAP Theorem** stated that one must choose between system responsiveness (availability) and data consistency in such distributed systems.


Classical relational database systems such as Oracle, MySQL, Postgres, and Microsoft SQL Server provided strong consistency but did not support distributed architectures.

This gap gave rise to a generation of data systems in the 2000s and 2010s with weaker consistency models in order to achieve high responsiveness in geographically distributed systems---the so-called **NoSQL** revolution.

Fortunately, a new generation of distributed database systems solved this problem through the use of data replication and consensus algorithms such as Paxos and Raft \sidecite{lamport2001paxos, ongaro2014search}.
Today's distributed database systems such as Spanner \index{Spanner} and CockroachDB \index{CockroachDB} maintain high levels of availability under strict consistency models.


DataJoint follows the classical ACID model for data consistency through the use of serializable transactions or modeled through the master-part relationship.
This is described in detail in \refsec{sec:transactions}.


## Databases in Science
Neuroscience researchers must process copious complex data while working in large multidisciplinary teams.
Certainly, they would benefit from using the best available tools for organizing, manipulating, analyzing, and quering data.
Yet today, few scientists use proper databases to manage data for their studies---a situation that has remained relatively unchanged for decades.
Instead, most scientists work with shared data in the form of files repositories organized into structured folders following some sort of a uniform naming convention.
Why do scientists avoid using databases to organize their daily work?

```{card}
Why scientists avoid databases
^^^
The 2005 technical report "Scientific Data Management in the Coming Decade" by Gray \emph{et al.}\ \sidecite{gray_scientific_2005} explored the reasons scientists cited for avoiding databases:

* We don't see any benefit in them. 
* They do not offer good visualization/plotting tools.
* I can handle my data in with my programming language.
* Databases do not support my data types (arrays, spatial, text, etc.)
* They do not support our access patterns.
* They are too slow. 
* We cannot manipulate data in databases with our standard application programs.
* Databases require expensive database administrators
```

These are valid points: conventional database systems are designed for business, commerce, and web applications, not scientific computing.
Scientists need different capabilities and extra degrees of freedom beyond conventional systems.
New database systems must evolve for greater flexibility, direct support of scientific data types, distributed computation and visualization.

## What's wrong with files?
What's wrong then with organizing data as a structured file repository?
When are files not good enough?

Files are simply strings of bytes with names.
No inherent structure or meta information.
They may be organized neatly and uniformly with smart naming conventions into structured folders---but those need to be agreed upon externally.
Many \emph{data standards} (such as BIDS\sidenote{Brain Imaging Data Structure (BIDS) data format: \url{https://bids.neuroimaging.io/}} for brain imaging) are defined simply in terms of formatted file/folder structures.
But in these cases the file system itself provides no mechanisms for enforcing structure---that's exactly why separate data standards must be created and followed.
File systems simply defer the challenges of efficient operations to the processes that use them.
Efficient work on data organized in files requires designing access patterns, creating indices for fast searches, and implementing common queries as a separate effort.
In shared distributed projects, additional effort must be spent on data transfers, enabling safe concurrent access and manipulations, and speeding up

These are valid points: conventional database systems are designed for business, commerce, and web applications, not scientific computing.
Scientists need different capabilities and extra degrees of freedom beyond conventional systems.
New database systems must evolve for greater flexibility, direct support of scientific data types, distributed computation and visualization.

What's wrong then with organizing data as a structured file repository?
When are files not good enough?

Files are simply strings of bytes with names.
No inherent structure or meta information.
They may be organized neatly and uniformly with smart naming conventions into structured folders---but those need to be agreed upon externally.
Many \emph{data standards} (such as BIDS\sidenote{Brain Imaging Data Structure (BIDS) data format: \url{https://bids.neuroimaging.io/}} for brain imaging) are defined simply in terms of formatted file/folder structures.
But in these cases the file system itself provides no mechanisms for enforcing structure---that's exactly why separate data standards must be created and followed.
File systems simply defer the challenges of efficient operations to the processes that use them.
Efficient work on data organized in files requires designing access patterns, creating indices for fast searches, and implementing common queries as a separate effort.
In shared distributed projects, additional effort must be spent on data transfers, enabling safe concurrent access and manipulations, and speeding up


