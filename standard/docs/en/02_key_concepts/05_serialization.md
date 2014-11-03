[TOC]

### Serializations

The Open Contracting Data Standard provides a **structured data model** for capturing in-depth information about all stages of the contracting process.** **

The current canonical version of this data model is provided by a **JSON Schema** which describes field names, field definitions and structures for the data. The compliance of data with the Open Contracting Data Standard will be assessed against this schema.

However, there are many use cases where publishers and users will want to work with data serialized in other formats. For this reason, the current version of OCDS supports a number of **secondary serializations **which are based on the canonical schema.

The two serialisations that will exist alongside the 1.0 RC are CSV Datapackage and Spreadsheet Workbook. These allow the majority of features of an contracting process to be represented using a selection of flat tables of data. They do not, however, currently support advanced features such as versioning.

These secondary serialisations act as a stepping-stone to generate fully structured open contracting data, or as a format for use when carrying out basic analysis.

**Single table CSV** 

 In a single flat table it is possible to represent a contracting process which has only one award, one contract, and one line-item and one attached document in each.

**  CSV Datapackage and Spreadsheet Workbook 
**By having a sub-table for each important object that can exist multiple times within a release, a greater degree of the structured data can be modelled. Sub-tables are provided for:

Awards

Contracts

Line Items

Documents

Classifications

Milestones

Both Datapackage and Workbook serialisations operate in a similar fashion, with the exception that the Spreadsheet Workbook combines a set of sub-tables into a single file, whereas the CSV Datapackage has a csv file for each sub-table.

We anticipate that a Linked Open Data serialisation of Open Contracting Data will also be available in the future, providing an ontology for representing Open Contracting Data, and a JSON-LD context for converting between JSON and RDF serialisations of the standard.

### Data packages

Whatever serialisation is used for Open Contracting Data, a single file may contain one or more release and records.

The release and record data package schemas describe the key meta-data that must be supplied for any file providing Open Contracting Data. This includes the publishedDate, publisher, uri for accessing the file, and the licensing details for the file.