# Preface 

This book teaches database programming for scientific applications.
Here, databases are used to communicate and enforce data structures that reflects the logic and flow of a scientific study shared among multiple collaborators.

Scientific databases must handle massive numerical arrays and complex data structures. 
Also, the data must be linked with the computational code used its processing and analysis. 
Code management must be combined with automated computations orchestrated on diverse computational platforms.

Today there exists a large variety of available data models and approaches for data management. 
Among these, relational databases provide the most principled and best established data model for structured data. 
The relational model provides a wide range machanism for data integrity and consistency, expressive and performant data queries, 
Remarkably, the entirity of the  relational data model is dominated by a single programming language---SQL---with sublanguages for data definition, queries, modifications, and procedures. 

Designed largely in the 1970s and 80s, with continual updates and improvements, SQL is one of the most successful standardization efforts. 

DataJoint provides a modern alternative to 

This books aims to provide a definitive summary of DataJoint principles and practice.
The book introduces general relational database programming in both DataJoint and SQL and I use the book to teach the {\em Database Systems} course at the University of St. Thomas in Houston.



## DataJoint History 

-- *by Dimitri Yatsenko*

```{image} ./images/cave-art.png
:alt: fishy
:class: bg-primary mb-1
:width: 400px
:align: center
```

In the autumn of 2009, while pursuing my graduate studies at Baylor College of Medicine (BCM), I began contemplating the potential of transforming database programming for use in scientific projects.
I wondered how to make the proper use of databases logical and accessible to research team managing data and computations.
It was then that I created the first rudimentary implementation of DataJoint for MATLAB and began using it for my own neurophysiology experiments.

A year prior, in 2008, I had joined the newly-established lab of Dr. Andreas S. Tolias in the Department of Neuroscience at BCM. 
The lab was seeking a robust approach to managing data and computations for the complex and vast data emerging from types of neurophysiology experiments such as calcium imaging. 
A few enterprising students in the lab, including Alex Ecker, Philipp Berens, Andreas Hoenselaar, and R. James Cotton, were building a framework named "Steinbruch". 
This was a MATLAB-centric library that harnessed the power of MySQL to streamline data, all interconnected through computational dependencies.

I envisioned a set of principles where database design adhered to the strictest principles, where data integrity was paramount and where every transaction was processed consistently. 
It became evident to me that conventional database models were missing a key ingredient: the formal notion of computational dependencies. 
This gap needed bridging, and that's precisely what I aimed to achieve with DataJoint.

After about a year of development, my labmates, starting with Manolis Froudarakis and Jacob Reimer, recognized the potential of DataJoint and began incorporating it into their work. 
Impressed by its practical utility, Dr. Tolias soon advocated its use for shared data analysis workflows. 
By 2011, DataJoint had woven itself into the fabric of our lab's operations, prompting me to release it as an open-source venture on [Google Code](https://code.google.com/archive/p/datajoint/).

Fast forward to 2014, when I was defending my thesis. DataJoint was no longer just a tool for our lab. It had found its way into multiple research labs globally. 
Notably, the first peer-reviewed studies employing DataJoint originated from the labs of Laura Busse and Steffen Katzner at the University of Tübingen, Germany, in 2013.

The evolution of DataJoint didn't stop there. 
Although it started as a MATLAB-centric tool, I began crafting a Python version by 2011. 
This effort gained traction when Edgar Y. Walker and Fabian Sinz collaborated in 2014 and 2015 to transform DataJoint into a comprehensive Python package. 
This would soon become the reference implementation for DataJoint.

I continued my postgraduate journey at BCM as the Tolias embarked on the [IARPA MICrONS project](https://www.iarpa.gov/research-programs/microns)---Machine Intelligence from Cortical Networks. 
There DataJoint proved instrumental for coordinating the work of a distributed and a multidisciplinary team, further spreading its adoption.

The evolution of DataJoint took another significant turn in October 2016. 
Four members from the Tolias lab---Dimitri Yatsenko, Jacob Reimer, Edgar Y. Walker, and Andreas S. Tolias---established Vathes LLC. 
This was in response to a funding opportunity from DARPA that aimed to commercialize tools tailored for neuroscience data management. 
In 2017, Vathes was awarded a hase I SBIR grant to explore the commercial potential of DataJoint. 
I led the the company as president and principal investigator. 
While Edgar and I balanced our roles at the company with our academic endeavors, we began expanding our team. 

Despite not securing the Phase II award that year, the initial months were promising. 
Vathes secured deals with several large multi-lab projects such as the Mesoscale Activity Project, the BrainCOGS Project at the Princeton Neuroscience Institute, The Moser Group in Norway, and the International Brain Lab. 
These collaborations enriched the Vathes team's understanding of data-driven team projects' effective organization.
In particular, Prof. Carlos Brody at Princeton University allocated a portion of his grant to enhance DataJoint documentation and tutorials while Prof. Karel Svoboda, then at the Janelia Research Campus, directed additional resources to create a showcase of DataJoint pipelines from a number of studies from his group.
Several scientists and engineers joined Datajoint and made significant contributions in this period: Thinh Nguyen, Raphael Guzman, Shan Shen, and Christopher Turner.

2020 was another pivotal year for DataJoint. 
The company secured a substantial five-year NIH grant of nearly $3.8 million to define DataJoint-based workflows for core neurophysiology experiments, leading to the inception of [DataJoint Elements](https://datajoint.com/elements). 
That same year, I transitioned to focus solely on Vathes, leaving BCM behind. 
Edgar balanced his roles for another year before leaving the company to fully immerse himself in academic pursuits.
Dr. Kabilar Gunalan joined the company, managing the development and dissemination of DataJoint Elements.

In January 2021, I proposed a fresh direction for the company, emphasizing commercial technology tailored for collaborative research. 
This vision necessitated reshaping Vathes into a corporation with a well-defined mission, transparent governance, and a more professional team. 
Throughout 2021, the company metamorphosed into a lean startup, assembling a dynamic engineering team. 
The goal was clear: find a product-market fit for a scalable DataJoint-based collaboration platform for collaborative data pipelines based on open-source software.
To align with its flagship product, the company rebranded itself as **DataJoint**.
By this time, DataJoint software had been adopted by dozens of neuroscience labs while the company provided direct services to several multi-lab consortia.

In 2022, the NIH awarded DataJoint another grant, now to develop an online platform to host and operate collaborative data pipelines for scientific projects.
With the additional funding, the team added seasoned executives and professional developers to lead product development and commercialization, in particular Jason Kirkpatrick joined as Chief Operating Officer and Monty Kosma as Chief Product Officer. 
Their leadership substantially accelerated the commercial product development.

I intend this book to be a living tutorial for the fundamental principles.

