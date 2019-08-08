---
copyright:
  years: 2019
lastupdated: "2019-04-15"

keywords: returns options, IBM Cloud, Insights for Medical Literature

subcollection: wh-iml

---
{:pre: .pre}
{:url: data-credential-placeholder='url'}
{:apikey: data-credential-placeholder='apikey'}
{:corpus: data-credential-placeholder='corpus'}
{:attribute-id: data-credential-placeholder='attribute-id'}
{:hide-dashboard: .hide-dashboard}
#Return more than documents
{: #returns-options}
The {{site.data.keyword.wh-iml_short}}  service Search API will return a list of document ids and titles when searching a corpus.  There are a number of other types of return objects that can be specified in place of or in addition to documents.  Several of the examples provided reference corpora, ontologies, and semantic types.  To see how to determine what corpora, ontologies, and semantic types are in your instance visit the [API documentation](https://test.cloud.ibm.com/apidocs/wh-iml).

When entering a command replace '[apikey]', '{url}', and '{corpus}' with your actual API key, instance URL, and targeted corpus.  Omit the braces from the command as they indicate a variable value.

##Returning cooccurring ontology artifacts
{: #cooccurring-artifacts}
The IML service has to ability to determine a set of ontology artifacts that are found in the same result set of one or more ontology artifacts or interest.  This feature can be used to deliver insights into potential relationships between artifacts like what diseases, drugs, genes, etc are found in the same documents as symptom or condition.  To retrieve a list of ontology artifacts simply add a returns block specifying the ontology of interest, corpora scope, and number of artifacts to return in the search request body.
```
{...
  "returns": {
    "concepts": {
      "ontology": "umls",
      "limit": 512,
      "scope": "corpus"
    },
    "documents": {
        "limit": "100",
        "offset": 0
    }...
```
{: pre}

##Returning a date histogram
{: #date-histogram}
The service has the ability to produce a histogram indicating the number of documents per year over a result set.  To retrieve a date histogram simply define a histogram block to the returns block in the search request body or add the histogram block to an existing query with a returns block.
```
curl -X POST -u "apikey:{apikey}" \
--header "Content-Type: application/json" \
--header "Accept: application/json" -d "
{
    "returns": {
       "dateHistograms": {
            "publishDate": {
                "interval": "1y",
                "utc": "-6"
            }
        }
    }
}" "{url}/wh-iml/api/v1/corpora/{corpus}/search?version=2019-04-15&verbose=false"
```
{: pre}

##Returning aggregations
{: #aggregations}
An aggregated list of unique values for document fields and their frequency of occurrence through the corpus can be retrieved from the service.  To receive an aggregated list of field values specify an aggregations block in the return block specifying the field name and number of aggregations (limit 100,000) to return.
```
curl -X POST -u "apikey:{apikey}" \
--header "Content-Type: application/json" \
--header "Accept: application/json" -d "
{
    "returns": {
        "aggregations": {
            "authors": {
                "limit": "100"
            }
        }
    }
}" "{url}/wh-iml/api/v1/corpora/{corpus}/search?version=2019-04-15&verbose=false"
```
{: pre}

##Returning attributes
{: #attributes}
Attributes are an unique cognitive artifact that is included as part of the default corpus enrichment.  Attributes combine semantic types, semantic concepts, and user defined ontologies and artifacts into a single searchable entity.  To retrieve a list of attributes that were found in the corpus and their frequency occurrance specify an annotations block in the returns block of the search API.
```
curl -X POST -u "apikey:{apikey}" \
--header "Content-Type: application/json" \
--header "Accept: application/json" -d "
{
    "returns": {
        "attributes": {
        }
    }
}" "{url}/wh-iml/api/v1/corpora/{corpus}/search?version=2019-04-15&verbose=false"
```
{: pre}
{: hide-dashboard}  

##Returning attribute values
{: #attribute-values}
Individual values that comprise an attribute (explained in the preceding section) and found in the corpus can be discovered by specifying the values block in the returns block supplying the attribute unique identifier and corpora scope.
```
curl -X POST -u "apikey:{apikey}" \
--header "Content-Type: application/json" \
--header "Accept: application/json" -d "
{
    "returns": {
        "values": {
            "attributeId": "(attribute-id)",{: attribute-id}
            "scope": "corpus"                
        }
    }
}" "{url}/wh-iml/api/v1/corpora/{corpus}/search?version=2019-04-15&verbose=false"
```
{: pre}
{: hide-dashboard}  

##Returning type ahead suggestions
{: #type-ahead}
A full or partial phrase can be passed and the service will return a list of ontology artifacts that are an exact match, begin with or contains the phrase.  The ontology artifacts are scoped to a particular ontology and can be further refined to semantic types within the ontology.  To retrieve a list of ontology artifact suggestions that can be provided in a type-ahead experience specify the typeahead block in the returns block specifying the phrase, ontology, number of matches to return and whether to include duplicate artifacts (artifacts with same synonyms).
```
curl -X POST -u "apikey:{apikey}" \
--header "Content-Type: application/json" \
--header "Accept: application/json" -d "
{
    "returns": {
        "typeahead": {
            "query": "sea",
            "limit": "20",
            "noDuplicates": true                
        }
    }
}" "{url}/wh-iml/api/v1/corpora/{corpus}/search?version=2019-04-15&verbose=false"
```
{: pre}
{: hide-dashboard} 

##Returning document passages
{: #passages}
Individual passages that comprise a document section can be retrieved along with the specific annotations for each passage.  To retrieve passages and their annotations add the passages block to go along with the documents block in the returns block.
```
{...
  "returns": {
    "documents": {
        "limit": "10",
        "offset": 0
    },
    "Passages": {
      "Limit": 3
    ...
    }
  }
}
```
{: pre}

The search API can be configured to return a variety of output with a single invocation.