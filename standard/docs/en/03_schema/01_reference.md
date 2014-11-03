[TOC]

# Schema Reference

<span class="lead">The [OCDS Schema pages](ToDo) provides a detailed specification of the fields and data structures to use when publishing data. This reference section works step-by=step through additional supporting information to assist publishers and users of the data.</span>

## Release structure

The majority of OCDS data is held within a structured [release](ToDo). Releases must be published within a release package. Releases are made up of a number of blocks of data, including:

* tender
* award
* contract
* performance

A release can only contain one set of tender information (as we define a unique [contracting process](../../definitions#contracting-process) by the initiation stage), but may contain multiple instances of awards, contracts and performance information.

Releases are given a [tag](#release-tag) to indicate what stage of a contracting process they represent, but there are no formal restrictions on when information about a stage of the contracting process may be provided. For example, a publisher announcing the signing of a contract with a 'contract' tagged release, may also include information in the award and tender blocks in order to provide a comprehensive picture of the contracting process to date which led to that contract being signed. 

### Package Metadata

A release package, modelled on the [Data Package](http://dataprotocols.org/data-packages/) protocol, provides meta-data about release(s) it contains. 

#### URI

Fieldname: uri (ToDo: Should I include this?)

The URI should unique identify this release package. Publishers should provide a dereferenceable HTTP URI wherever possible and should host the data package at this URI, enabling users to look-up and verify the contents of a release package from its original source. 

#### Published Date

Fieldname: publishedDate (ToDo: Should I include this?)

The [date](#date) on which this package was published.

If a package is automatically generated and re-published on a regular basis, this date should reflect the date of the last change to the contents of the package. 

#### Publisher

Fieldname: publisher

An identifier for the publisher. See the [Organization/Entity](#entity) guidance for details.

#### License

Fieldname: license

See the [licensing guidance](../../implementation/publication_patterns#licensing) for more details on selecting and publishing license information. 

#### Publication Policy

Fieldname: publicationPolicy

See the [publication policy](../../implementation/publication_patterns#publication-policy) guidance for more details.

### Top level fields

#### OCID

Providing each [contracting process](../../definitions#contracting-process) with a unique identifier is essential to enable data about contracts to be linked up across different releases.

Open Contracting IDs are composed of a prefix assigned to each publisher, and a local identifier drawn from their internal systems that can be used to tie together tenders, awards, contracts and other key data points from a specific contracting process.

See the [Open Contracting Identifier guidance](../../identifiers#ocid) for details of how to construct an OCID. 

#### Release date

The release [date](#date) should reflect the point in time at which the information in this release was disclosed. 

A release package may contain release with different release dates.

#### formationType (ToDo: check - should this be initiationType?)

Contracts may be formed under a number of different processes. 

Values must be drawn from the [formationType codelist](../codelists#formationType)

Currently, only 'tender' is supported. 

#### Tag (ToDo: Check Title)

The release tag is used to identify the nature of the release being made. 

This can be used by consuming applications to filter releases, or may in future be used for advanced validation.

A release which updates or amends previous data must always use the appropriate update or amendment release tag. 

Values must be drawn from the [releaseTag codelist](../codelists#releaseTag).

#### Language

See the section on [multi-language support](#multi-language-support) for details.

#### Buyer

Published using an [organization](#entity) block.

### Tender

The tender section includes details of the announcement that a organization intends to source some particular goods or services, and to establish one or more contract(s) for these.

It may contain details of a forthcoming process to receive and evaluate proposals to supply these goods and services, and may also be used to record details of how a completed tender process, including details of bids received. 

#### Tender ID

#### Procuring Entity

#### Attachments

#### Items

#### Value

#### Procurement Method

#### Selection Criteria

#### Selection Details

#### Submission Method

#### Submission Details

#### Tender Period

#### Clarification Period

#### Clarifications

#### Award Period

#### Bidders

ToDo: Check if numberOfBidders and numberOfBids included



### Award



### Contract


### Implementation


## Record structure



## Multi-language support

Many publishers need to be able to share key data in multiple languages. All free-text title and description fields in the Open Contracting Data Standard can be given in one or more languages.

Every OCDS release or record should include a default language in the ```language``` field. 

Languages can be identified using language tags taken from [BCP47](http://tools.ietf.org/html/bcp47) in order to accomodate variations in dialect. However, publishers *should *use the two letter [ISO-639-1 two-digit language tags](http://en.wikipedia.org/wiki/List_of_ISO_639-1_codes) in the vast majority of circumstances, considering that users will not generally need to distinguish between, for example, en_US and en_GB. 

To include a language variation of a field, the field name should be suffixed with _ and the appropriate language tag. For example: ‘title_es’ for Spanish.

The JSON Schema makes use of the JSON Scheme 0.4 [‘Pattern Properties](http://spacetelescope.github.io/understanding-json-schema/reference/object.html#pattern-properties)’ definition to allow validation of multi-language fields. 

**Worked example: **

A contract is for ‘Software consultancy services’ may be published in a release with the default language sent to ‘en’ (the ISO-639-1 code for English). The following examples give the description of an item as English, French and Spanish.



**	[JSON]**

**	**{

**	**"language": “en”,

	"tender": {

**	"**item":** **{

			"description":”Software consultancy services”

			"description_es":”Servicios de consultoría en software”,

		"description_fr":”Services de conseil en logiciels”

		}

**	**}

	}

**[CSV] **

	| language | tender.item.description | tender.item.description_es | tender.item.description_fr |

	| --- | --- | --- | --- |

	| en | Software consultancy services | Servicios de consultoría en software | Services de conseil en logiciels |

See [https://github.com/open-contracting/standard/issues/64](https://github.com/open-contracting/standard/issues/64)


## Field reference

### Entity

### Date

[https://github.com/open-contracting/standard/issues/67](https://github.com/open-contracting/standard/issues/67) 

### Item

### Milestone

### Value

### Location




