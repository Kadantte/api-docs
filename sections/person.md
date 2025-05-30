# Person

Contains information on entities that have some association to works of art in the collection or publications. Associations include artists, sitters, printers, donors, authors, publishers, and more.

## Get people

`GET /person` will get all people affiliated with the museums.

Include one or more of the following parameters to filter the items.

| Parameter | Value |
| :--------- | :----- |
| apikey | YOUR API KEY ***required*** |
| q | FIELD:VALUE (see [Elasticsearch Query String syntax](https://www.elastic.co/guide/en/elasticsearch/reference/7.17/query-dsl-query-string-query.html) for more options) |
| size | 0-9+ |
| page | 0-9+ |
| sort | FIELD NAME or "random" or "random:[SEED NUMBER]" |
| sortorder | asc or desc |
| fields | comma separated list of data fields you want in the output |
| aggregation |  see [Elasticsearch aggregations](http://www.elastic.co/guide/en/elasticsearch/reference/7.17/search-aggregations.html#_structuring_aggregations) |
| id | pipe separated list of record IDs |

#### Examples

> https://api.harvardartmuseums.org/person?q=culture:Dutch  
> Finds all of the people that are Dutch.    

#### Response

```json
{
    "info": {
        "totalrecordsperquery": 10,
        "totalrecords": 600,
        "pages": 60,
        "page": 1,
        "next": "https://api.harvardartmuseums.org/person?q=culture%3ADutch&size=10&page=2",
        "responsetime": "6 ms"
    },
    "records": [
        {
            "gender": "male",
            "displaydate": "1872 - 1944",
            "objectcount": 10,
            "roles": [
                {
                    "role": "Related name",
                    "context": "object",
                    "frequency": 5
                },
                {
                    "role": "Author",
                    "context": "object",
                    "frequency": 1
                },
                {
                    "role": "Artist",
                    "context": "object",
                    "frequency": 19
                },
                {
                    "role": "Artist after",
                    "context": "object",
                    "frequency": 2
                }
            ],
            "wikidata_id": "Q151803",
            "dateend": 1944,
            "url": "https://www.harvardartmuseums.org/collections/person/27650",
            "names": [
                {
                    "displayname": "Piet Mondrian",
                    "type": "Primary Name"
                },
                {
                    "displayname": "Pieter Cornelis Mondriaan",
                    "type": "Alternate Name"
                },
                {
                    "displayname": "Piet Mondriaan",
                    "type": "Alternate Name"
                }
            ],
            "birthplace": "Amersfoort, The Netherlands",
            "datebegin": 1872,
            "culture": "Dutch",
            "displayname": "Piet Mondrian",
            "alphasort": "Mondrian, Piet",
            "ulan_id": "500004972",
            "personid": 27650,
            "deathplace": "New York, N.Y.",
            "id": 27650,
            "lastupdate": "2023-07-16T13:53:36-0400",
            "lcnaf_id": "n79135254"
        },
        {
            "gender": "male",
            "displaydate": "1606 - 1669",
            "objectcount": 709,
            "roles": [
                {
                    "role": "Related name",
                    "context": "object",
                    "frequency": 222
                },
                {
                    "role": "Previous attribution",
                    "context": "object",
                    "frequency": 10
                },
                {
                    "role": "Artist",
                    "context": "object",
                    "frequency": 291
                },
                {
                    "role": "Artist after",
                    "context": "object",
                    "frequency": 233
                }
            ],
            "wikidata_id": "Q5598",
            "dateend": 1669,
            "url": "https://www.harvardartmuseums.org/collections/person/28241",
            "viaf_id": "64013650",
            "names": [
                {
                    "displayname": "Rembrandt van Rijn",
                    "type": "Alternate Name"
                },
                {
                    "displayname": "Rembrandt Harmensz. van Rijn",
                    "type": "Primary Name"
                },
                {
                    "displayname": "Rembrandt",
                    "type": "Alternate Name"
                }
            ],
            "birthplace": "Leiden",
            "wikipedia_id": "4254144",
            "datebegin": 1606,
            "culture": "Dutch",
            "displayname": "Rembrandt Harmensz. van Rijn",
            "alphasort": "Rembrandt Harmensz. van Rijn",
            "ulan_id": "500011051",
            "personid": 28241,
            "deathplace": "Amsterdam",
            "id": 28241,
            "lastupdate": "2023-07-16T13:54:11-0400",
            "lcnaf_id": "n79142935"
        }
    ]
}
```

## Get person

`GET /person/PERSON_ID` will get detailed info about a specific person.

**alphasort** describes the form of the persons name useful for sorting names alphabetically  
This often takes the form of "lastname, firstname" and is our preferred way to sort names.  

**createdate** describes the date and time the record was created in the museum's electronic catalogue system   

**displayname** describes the form of the persons name used for display purposes  
This often takes the form of "firstname lastname" and is our preferred way to display names.  

**names** describes the variant names of the person  
A person may have one or more names.

`displayname` - is the displayable variant name    
`type` - is the type of variant name, such as 'Original Language Name' or 'Alternate Name'  

**personid** describes the numeric unique identifier for a record    

**roles** describes the roles occupied by the person in the context of the Harvard Art Museums collections and activities

Some fields contain numeric values that have special meaning and can help connect our records to other data sets. Not all records have these fields because we couldn't always find a match.  

**lcnaf_id** contains the identifier for the matching entry in [LCNAF](https://id.loc.gov/authorities/names)

**ulan_id** contains the identifier for the matching entry in the [ULAN](http://www.getty.edu/research/tools/vocabularies/ulan/) vocabulary

**viaf_id** contains the identifier for the matching entry in [VIAF](https://viaf.org/)

**wikidata_id** contains the identifier for the matching entry in [Wikidata](https://www.wikidata.org/)

**wikipedia_id** contains the identifier for the matching entry in [Wikipedia](http://www.wikipedia.org/)

#### Examples

> https://api.harvardartmuseums.org/person/29481  
> Returns the full record for Utagawa Yoshikazu.

#### Response

```json
{
    "id": 29481,
    "personid": 29481,
    "displayname": "Utagawa Yoshikazu",
    "datebegin": 1850,
    "dateend": 1870,
    "displaydate": "active 1850 - 1870",
    "culture": "Japanese",
    "gender": "male",
    "birthplace": null,
    "deathplace": null,
    "alphasort": "Utagawa, Yoshikazu",
    "url": "https://www.harvardartmuseums.org/collections/person/29481",
    "objectcount": 50,
    "lastupdate": "2023-07-16T13:52:05-0400",
    "viaf_id": "252063172",
    "ulan_id": "500334458",
    "wikidata_id": "Q11545174",
    "names": [
        {
            "displayname": "一川芳員",
            "type": "Original Language Name"
        },
        {
            "displayname": "Utagawa Yoshikazu",
            "type": "Primary Name"
        }
    ],
    "roles": [
        {
            "role": "Artist",
            "context": "object",
            "frequency": 135
        }
    ]
}
```
