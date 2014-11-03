[TOC]

# Schema Reference

<span class="lead">The [OCDS Schema pages](ToDo) provides a detailed specification of the fields and data structures to use when publishing data. This reference section works step-by=step through additional supporting information to assist publishers and users of the data.</span>

## Release structure

A structured [release](ToDo) 


### Package Metadata


### Top level fields

#### OCID

#### Date

#### Tag (ToDo: Check Title)

#### Language

#### Buyer

#### formationType


### Tender


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

### Dates

[https://github.com/open-contracting/standard/issues/67](https://github.com/open-contracting/standard/issues/67) 

### Items

### Milestones

### Values

### Locations




