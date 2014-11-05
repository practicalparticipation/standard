[TOC]

See [https://github.com/open-contracting/standard/issues/64](https://github.com/open-contracting/standard/issues/64)



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

Whereas there can be multiple releases concerning a given contracting process, there is a single **contracting record** for each OCID, providing a summary of all the available data about this particular contracting process.

Releases MUST contain:

* An [OCID](../../key_concepts/identifiers#ocid)
* An array of **releases** related to this contracting process - either by providing a URL for where these releases can be found, or embedding a full copy of the release

Release SHOULD contain:

* **compiledRelease** - the latest version of all open contracting process fields, represented using the release schema. For example, if a contractSignature release has been issued with with a contractValue of $100, and then a contractAmendment release has been issued with a contractValue updated to $200, the compiledRelease would have contract/contractValue of $200.

and

* **versionedRelease** - containing the history of the data in the compiledRecord, with all known past values of any field and the release that information came from.

Records should be embedded within a record package.  

### Package meta-data

ToDo

### Top Level Fields

#### Packages

### Records

An array of one or more records, consisting of the following sections:

* Releases (required)
* Compiled Release (optional)
* Versioning Release (optional)

#### Releases

The releases that go to make up a contracting process can be provided in two ways:

* URLs for each release
* Embedded copies of the release

If providing and array of URLs, it should be possible for a consuming application to look up each URL, retrieve a release package, and locate the release inside it. 

In order to locate the specific release inside a release package the releaseID of the release should be appended to the package URL using a fragment identifier.

For example:

* http://ocds.open-contracting.org/demos/releases/12345.json#ocds-a2ef3d01-1594121/1 to refer to the release with releaseID:ocds-a2ef3d01-1594121/1 

ToDo: Construct these as real examples.

#### Compiled Release

#### Versioned Release




## Multi-language support

ToDo: - CHECK RESOLUTION OF https://github.com/open-contracting/standard/issues/21

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



## Field reference

### Entity




### Date

ToDo: Embed block of schema.

OCDS makes use of [ISO8601](http://en.wikipedia.org/wiki/ISO_8601) date-times, following [RFC3339 §5.6](http://tools.ietf.org/html/rfc3339#section-5.6).

A time and timezone/offset MUST always be provided in a date-time.

The following are valid date-times:

* '2014-10-21T09:30:00Z' - 9:30 am on the 21st October 2014, UTC
* '2014-11-18T18:00:00-06:00' - 6pm on 18th November 2014 CST (Central Standard Time)

The following are not valid:

* '2014-10-21' - Missing time portion
* '2014-10-21T18:00' - missing seconds in time portion.
* '2014-11-18T18:00:00' - Missing timezone/offset portion
* '11/18/2014 18:00' - Not following the pattern at all!

Accurately including the time and timezone offsets is particular important for tender deadlines and other dates which may have legal significance, and where users of the data may be from different timezones. The character Z on the end of a date-time indicates the [UTC](http://en.wikipedia.org/wiki/Coordinated_Universal_Time) (or Zero offset) timezone, whereas other timezones are indicated by their value '+/-hh:mm' UTC on the end of the date-time value. 

In the event that the system from which data is drawn only includes dates, and does not include time information, publishers should consider sensible defaults for each field. For example, the startDate time of a clarification period may be set to '00:00:00Z' to indicate that clarifications can be requested from any time on the date stated, with the endDate time set to 23:23:59Z to indicate that clarifications can be sent up until the end of the endDate given. Alternatively, if clarification requests are only accepted in standard office hours, these values might be 09:00:00Z and 17:00:00Z respectively. 

In the event that a date field is not bound to a specific time at all, publishers should choose a default time value of '23:23:59' and either 'Z' (for UTC) or the timezone of the publisher, indicating that the time refers to the end of the given date. 


### Item

### Milestone

### Value

### Location

Possible to specify location of:

* Line Items
* Overall contract

at the level of administrative geography. 



Based on conversations with Owen Scott the following points seem important for location:

(1) Latitude and longitude are generally not that useful, and are often misleading: locations can be an artefact of whatever geocoding process the publisher used, and most projects / contracts are not delivered at a point location. Rather, they are delivered in polygon spaces. 

(2) Much better is to focus on administrative geography levels, and entities like cities. These are identified using gazetteers.

(3) There is an important distinction between locations that **are** the administrative entity identified (e.g. the contract is to run waste collection for a given district), and location that are **within** an administrative entity (e.g. the contract is to build three schools in a district, but there are lots of other schools in the area too).

(4) There is no single uniform global gazetteer to draw upon, and the coverage of gazetteers and the availability of open boundary and other data to go with them varies from country to country.

This leads to a suggestion that our location property in an ideal world should consist of an array of objects, with properties to represent:

* Gazetteer - used to identify the source from which a geographic identifier will be drawn. See the IATI GeographicVocabulary codelist for reference
* Location Type - used to identify the kind of location being given, from a codelist including ADM0 - ADM10 (Administrative Levels), Entity or other
* Location - a code drawn from the gazeteer for this location
* Contain In / Is - a flag / enum list for whether the location is contained within the above gazetteer location, or is that location

In practice, allowing an array of objects does raise a slight challenge:

* The most natural place to attach location is to line-items (these are delivered at particular points) - but line-items do not have IDs, making the sub-table approach in flattened data difficult to achieve. (Solution: allow optional ids for line items?)

In this approach, a valid gazetteer might be 'ISO 3166' allowing the country of a contract to be specified via a location entry with ADM0 (Country level) and the country code. Equally, if Open Street Map is included as a gazetteer, pointers could be made to specific entities in a country where users want very detailed geocoding. 

The conversion of data to lat-lng or polygon maps would then be a third-party task using lookups. 

Given that addresses can be geocoded, and organisational identifiers should be possible to look-up and resolve to an organisation with an address (in theory... though not practice in many cases just yet) which can be geocoded, I'm not sure there is a strong case to include location at the organisation level. 

## Questions

Are there cases where a publisher would want to state the location of a contract, but not at the line-item level? i.e. should location also be possible to attach at the general tender / contract level?

