# The Relational Data Model 


The **relational data model** is the brainchild of the British-American mathematician and engineer [Edgar F. Codd.](https://amturing.acm.org/award_winners/codd_1000892.cfm), earning him the Turing Award.

Working at IBM, Codd explored the possibility of working on data using concepts from set theory  {cite:p}`codd_relational_1970`.
Codd was inspired by the concept of *set relations* and the \emph{calculus of relations} proposed by the British logician **Augustus De Morgan** and further developed by the American logician **Charles Sanders Peirce**  in the mid-XIX century {cite:p}`de1860syllabus`, {cite:p}`peirce1870description` --- theories rooted in well-established concepts of logic and set theory.
A mathematical **relation** is defined as a subset of the **Cartesian product** of multiple sets.
As with other types of sets in **set theory**, relations can be transformed and manipulated using set operators such as *union*, *intersection*, *difference*, *etc*.

Codd's model was largely derived from relational theory but differed sufficiently in its basic definitions to make a new type of algebra.
The relational data model gave mathematicians a rigorous theory for optimizing data organization and storage and to construct queries.
Through the 1970s, before relational databases became practical, theorists derived fundamental rules for rigorous data organization and queries from first principles using mathematical proofs and derivations.
For this reason, early work on relational databases has an abstract academic feel to it with rather simple toy examples: the ubiquitous employees/departments, products/orders, and students/courses.
The design principles were defined through the rigorous but rather abstract principles, the **normal forms** {cite:p}`kent1983simple`.

```{card}
Fundamentally, the **relational data model** is the view of data in the form of sets of like elements.
```

Relationships between data elements and rules of data integrity are expressed as constraints on set memberships.
Precise queries take the form of query expressions as opposed to other data models where data are queried by routines that traverse and aggregate the desired data; *i.e* **declarative** rather than **imperative** queries.

