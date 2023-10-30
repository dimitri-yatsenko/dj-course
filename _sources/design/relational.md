# The Relational Data Model 


The **relational data model** is the brainchild of the British-American mathematician and engineer [Edgar F. Codd.](https://amturing.acm.org/award_winners/codd_1000892.cfm), earning him the Turing Award.

Working at IBM, Codd explored the possibility of working on data using concepts from set theory  \sidecite{codd_relational_1970}.
Codd was inspired by the concept of \emph{set relations} and the \emph{calculus of relations} proposed by the British logician \emph{Augustus De Morgan} \index{De Morgan} and further developed by the American logician Charles Sanders Peirce \index{Peirce} in the mid-XIX century \sidecite{de1860syllabus, peirce1870description} --- theories rooted in well-established concepts of logic and set theory.
A mathematical \emph{relation} \index{relation} is defined as a subset of the \emph{Cartesian product} of two or more sets.
As with other types of sets in \emph{set theory}, relations can be transformed and manipulated using set operators such as \emph{union}, \emph{intersection}, \emph{difference}, \emph{etc.}.

Codd's model was largely derived from relational theory but differed sufficiently in its basic definitions to make a new type of algebra.
The relational data model gave mathematicians a rigorous theory for optimizing data organization and storage and to construct queries.
Through the 1970s, before relational databases became practical, theorists derived fundamental rules for rigorous data organization and queries from first principles using mathematical proofs and derivations.
For this reason, early work on relational databases has an abstract academic feel to it with rather simple toy examples: the ubiquitous employees/departments, products/orders, and students/courses.
The design principles were defined through the rigorous but rather abstract principles, the \emph{normal forms} \sidecite{kent1983simple}.

Fundamentally, the \textbf{\emph{relational data model}} \index{relational data model}  is the view of data in the form of sets (as in Set Theory) of like elements.
Relationships between data elements and rules of data integrity are expressed as constraints on set memberships.
Precise queries take the form of query expressions as opposed to other data models where data are queried by routines that traverse and aggregate the desired data; \emph{i.e.}\ \emph{declarative} rather than \emph{imperative} queries.
