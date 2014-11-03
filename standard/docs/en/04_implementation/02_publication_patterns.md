[TOC]

## Publication guidance

We have set out a 5* approach to progressively improving the publication of Open Contracting Data on the web. In this section we consider a number of publishing good practices and patterns.

### Publication policy

See [https://github.com/open-contracting/standard/issues/133](https://github.com/open-contracting/standard/issues/133) 

### Licensing data

**ToDo**

"description": "A link to the license that applies to the data in this datapackage. [Open Definition Conformant](http://opendefinition.org/licenses/) licenses are strongly recommended. The canonical URI of the license should be used. Documents linked from this file may be under other license conditions. ",

### Release URIs

See [https://github.com/open-contracting/standard/issues/31](https://github.com/open-contracting/standard/issues/31) 

**File segmentation**

The release and record data package containers (in JSON and CSV) offer a way to provide **bulk access** to a collection of contracting process release and records. However, very large files can be difficult for users to download and process.

The following section provides suggested good practices which will assist users in accessing data. These are not requirements of the standard, but are based on experiences of maximising the number of users able to work with datasets with their existing hardware and software. 

#### Limits

When generating data packages for bulk download, apply the following limits:

* Unzipped OCDS data packages should not exceed 1Gb each;

* Zipped OCDS data packages should not exceed 10 Mb each;

* A single OCDS data package should contain a maximim of 250,000 awards or contracts; 

When a file is likely to exceed one of these limits, release or records should be split across multiple files. Dynamically generated bulk downloads do not have to apply these limits, though publishers should consider ways to advise users when a query is likely to generate a very large file. 

Segmenting files

When the suggested limits require publication of multiple files, publishers should consider ways to split data across available files. 

For releases, publishers may choose to:

1. Segment by **releaseDate - **placing all the releases from a given day, month or year in the same file;

2. Segment by **contracting process identifier **- placing all the releases related to a given set of contract process identifiers together in the same data package;

For records, publishers should segment either based on the first **releaseDate** associated with a contracting process, or by **contracting process identifier.**

Following these approaches will avoid release and records moving between files. 

Compression

OCDS data packages may be compressed in order to save on diskspace and bandwidth. 

If compressing data packages, publishers *should* use the zip file format. 

#### Serving files

Publishers should ensure that the web server providing access to bulk files correctly reports the [HTTP Last-Modified](http://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html#sec14.29) header so that consuming applications only need to download updated files.

### Providing flat-file exports

### Supporting discovery with .well-known 

See [https://github.com/open-contracting/standard/issues/75](https://github.com/open-contracting/standard/issues/75) 
