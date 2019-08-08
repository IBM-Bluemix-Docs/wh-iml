---
copyright:
  years: 2019
lastupdated: "2019-03-26"

keywords: advanced invocations, IBM Cloud, Insights for Medical Literature

subcollection: wh-iml

---
{:pre: .pre}
{:url: data-credential-placeholder='url'}
{:apikey: data-credential-placeholder='apikey'}
{:corpus: data-credential-placeholder='corpus'}

#Advanced Invocations
{: #advanced-invocations}
The {{site.data.keyword.wh-iml_full}} (IML) service provides the solution with a variety of features and options to custom tailor the search experience to meet customer needs.  A number of examples are provided to demonstrate how to use additional IML features beyond a simple query.

When entering a command replace '[apikey]', '{url}', and '{corpus}' with your actual API key, instance URL, and targeted corpus.  Omit the braces from the command as they indicate a variable value.

##Searching across multiple corpora
{: #searching-multiple-corpora}
To search from articles across multiple corpora in your instance simply list the corpora delisted by a comma.
```
curl -X POST -u "apikey:{apikey}" --header "Content-Type: application/json" --header "Accept: application/json" -d "{
	"query": {
	    "concepts": [
	           {
	                "ontology": "umls",
	                "id": "C0024117",
	                "rank": "10",
	                "type": "DiseaseOrSyndrome",
	                "includeRelated": [],
	                "negated": false
	            }
	     ]
    },
     "returns": {
     	"documents": {
        	"limit": "10",
        	"offset": 0
    	}
    }
}" "{url}/wh-iml/api/v1/corpora/{corpus},{corpus}/search?version=2019-04-12&verbose=false"
```
{: pre}

The service returns a JSON object that lists the ontology artifacts found in the corpora that match or contain the original phrase and additional metadata including the article identifier, title, and ontology source.

##Searching multiple corpora weighted
{: #searching-multiple-corpora-weighted}
When searching multiple corpora a weight can be assigned to each corpus telling IML how to rank results from the corpora.  To assign a weight to a corpus append colon and a number between 1 and 10.  The higher the weight assigned to the corpus the more likely it's matches will be the first entries in the search results.  The following example will return clinical trial results before abstracts.
```
curl -X POST -u "apikey:{apikey}" --header "Content-Type: application/json" --header "Accept: application/json" -d "{
    "query": {
	    "concepts": [
	           {
	                "ontology": "umls",
	                "id": "C0024117",
	                "rank": "10",
	                "type": "DiseaseOrSyndrome",
	                "includeRelated": [],
	                "negated": false
	            }
	     ]
    },
     "returns": {
     	"documents": {
        	"limit": "10",
        	"offset": 0
    	}
    }
}" "{url}/wh-iml/api/v1/corpora/{corpus}:5,{corpus):10/search?version=2019-04-12&verbose=false"
```
{: pre}

##Filtering search results
{: #filtering-search-results}
Search results can be filtered using fields that are known to exist in the default corpora or if using a custom plan fields specific to custom instance.  There are three fields common across the default corpora that can be used to filter search results:
- publication name
- publication date
- author

###Filtering by publication name
{: #publication-filtering}
Search results can be filtered by adding a boolTerm object to the body of the search request.  The boolTerm object specifies the field name and value(s) to filter on.
```
curl -X POST -u "apikey:{apikey}" --header "Content-Type: application/json" --header "Accept: application/json" -d "{
    "query": {
	   "concepts": [
	           {
	                "ontology": "umls",
	                "id": "C0024117",
	                "rank": "10",
	                "type": "DiseaseOrSyndrome",
	                "includeRelated": [],
	                "negated": false
	            }
	    ],
            "boolTerm": {
              "provider": "The Journal of biological chemistry" OR "British Medical Journal"
            }
    },
     "returns": {
     	"documents": {
        	"limit": "10",
        	"offset": 0
    	}
    }
}" "{url}/wh-iml/api/v1/corpora/{corpus}/search?version=2019-04-12&verbose=false"
```
{: pre}

###Filtering by publication date
{: #date-filtering}
Search results can be filtered by specifying a publication date range in the body of the search request.  The publication date filter criteria are expressed as a beginning and ending year to define the span of desired results.
```
curl -X POST -u "apikey:{apikey}" --header "Content-Type: application/json" --header "Accept: application/json" -d "{
    "query": {
	    "concepts": [
	           {
	                "ontology": "umls",
	                "id": "C0024117",
	                "rank": "10",
	                "type": "DiseaseOrSyndrome",
	                "includeRelated": [],
	                "negated": false
	            }
	     ],
           "dateRange": {
             "publishDate": {
               "begin": "2014",
               "end": "2018"
             }
           }
    },
     "returns": {
     	"documents": {
        	"limit": "10",
        	"offset": 0
    	}
    }
}" "{url}/wh-iml/api/v1/corpora/{corpus}/search?version=2019-04-12&verbose=false"
```
{: pre}

The search API is very flexible and can be configured to satisfy a large variety of use cases.