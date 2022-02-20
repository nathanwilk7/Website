---
layout: plain
title: GSoC Project Ideas
---

Below, you can find some ideas on the directions in which we could jointly push Polypheny forward. Please consider them as starting points for your proposal. Of course, if you have other ideas, we would be very happy to hear them. Feel free to [contact us](/community/gsoc/#contact) and get feedback on what you plan to do beforehand.

Simply copying and pasting one of the ideas will not work. On the other hand, creating a completely new idea without first [consulting](/community/gsoc/#contact) the mentors might be difficult as well.
{:.message}

* this unordered seed list will be replaced by toc as unordered list
{:toc}



## Data Source Adapter for Excel Sheets
Data source adapters allow to map existing data into the schema of Polypheny-DB. This allows to query the mapped data using the available query languages and features of Polypheny-DB. Furthermore, imported tables can be joined with other tables. The goal of this project is to add an adapter similar to the CSV adapter but for Excel files. You can also come up with your own idea for a data source adapter. Data source adapters do not necessarily need to support data modification queries.

**Difficulty**: easy  
**Size**: medium (~175 hours)



## Data Source Adapter for Google Sheets
This project is similar to the data source adapter for Excel sheets. However, the idea of this project is to build an adapter for Google Sheets. There is an API for Google Sheets that allows reading and manipulating sheets. It is possible to combine this project idea with the adapter for Excel sheets, making it a large (~350 hours) project.

**Difficulty**: easy-medium  
**Size**: medium (~175 hours)




## Export Function for Schema and Data
The Polypheny-UI does not yet provide an option to export one or multiple entities (tables, collections, ..) or whole schemas into one file. However, such a feature is very handy and would be a valuable addition to Polypheny-UI. The project can be extended to a large project by considering features like compression and additional optimizations for faster import of these scripts.

**Difficulty**: medium  
**Size**: medium (~175 hours)




## SPARQL Support for Polypheny 
SPARQL is a query language for RDF graphs. It is one of the key technologies of the semantic web. The idea of this project is to add native support for SPARQL to Polypheny-DB. 

**Difficulty**: hard  
**Size**: large (~350 hours)



## CouchDB-like HTTP Query Interface
CouchDB is a popular document-oriented database system. It features an HTTP query interface that allows querying and manipulating data. The idea of this project is to build a query interface for Polypheny that adheres to the specification of the CouchDB query API. This would allow to seamlessly replace an CouchDB database with Polypheny or to use applications written for ChouchDB with Polypheny.

**Difficulty**: medium-hard  
**Size**: large (~350 hours)




## Better Visualization of Query Plans
Polypheny visualizes query plans in its user interface. Although this feature is very powerful and provides various insights, there is potential for visual improvements. This project idea is about visually improving the plan view. This might include adding the estimated number of row to the edges or making the thickness of the edges depending on it. A proposal for this project idea should include a concept on the planned changes.

**Difficulty**: easy  
**Size**: medium (~175 hours)




## Railroad Diagrams for Language Syntax
Railroad (or syntax) diagrams are a powerful and easy to comprehend way for representing grammars. The idea of this project is to build a system for the Polypheny website that integrates into the Jekyll process and allows visualizing the syntax of the supported query languages using railroad diagrams. 

**Difficulty**: medium  
**Size**: medium (~175 hours)




## Driver for Go, C++, PHP, ...
Currently there is a JDBC driver and a Python connector for Polypheny-DB. In this project, support for other languages or frameworks shall be added. This project is explicitly for developers with experience with interacting with databases in a specific language or framework. Feel free to link references to experience with that language or framework in your proposal. 

**Difficulty**: medium  
**Size**: medium (~175 hours)




## Server-side Query-to-File
For some applications, especially for those making use of the multimedia and file storage capabilities of Polypheny-DB, it is useful to represent and interact with a table (or the result of an arbitrary query) as file system. With _Query to File_ we already have a prototype implementation of this using FUSE and running on the client computer. The idea of this project is to integrate this concept directly into Polypheny-DB. Instead of an application running on the local machine, Polypheny-DB should provide a FTP or WebDAV share that could then be mounted on other machines.

**Difficulty**: medium-hard  
**Size**: large (~350 hours)

