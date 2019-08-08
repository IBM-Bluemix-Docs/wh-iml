---
copyright:
  years: 2019
lastupdated: "2019-04-12"

keywords: getting started tutorial, IBM Cloud, Insights for Medical Literature

subcollection: wh-iml

---
{:pre: .pre}
{:url: data-credential-placeholder='url'}
{:apikey: data-credential-placeholder='apikey'}
{:corpus: data-credential-placeholder='corpus'}
{:hide-dashboard: .hide-dashboard}

# Getting started tutorial
{: #getting-started}

The {{site.data.keyword.wh-iml_full}} (IML) service derives insights about medical literature that has been cognitively analyzed by a medical ontology.  This tutorial can help you get started quickly with the Insights for Medical Literature service.  The examples show you how to call the service APIs to issue a query and retrieve a set of relevant articles for review.

When entering a command replace '[apikey]', '{url}', and '{corpus}' with your actual API key, instance URL, and targeted corpus.  Omit the braces from the command as they indicate a variable value.  An actual invocation resembles the following example:
```
curl -X GET -u "apikey:L_HALhLVIksh1b73l97LSs6R_3gLo4xkujAaxm7i-b9x" \
--header "Accept: application/json" \
"https://gateway.watsonplatform.net/api/v1/corpora?version=2019-03-28&verbose=false"
```
{: pre}
{: hide-dashboard}

## Before you begin
{: #prereqs}
You need an {{site.data.keyword.cloud}} account, an instance of {{site.data.keyword.wh-iml_short}}, and Curl installed on your local workstation.
{: hide-dashboard}

## Step 1.  Discover what corpora are available for the instance
{: #discover_corpora}
The first example calls the GET /v1/corpora method and requests a JSON response.

```
curl -X GET -u "apikey:{apikey}" \
--header "Accept: application/json" \
"{url}/api/v1/corpora?version=2019-03-28&verbose=false"
```
{: pre}

The service returns a JSON object that lists the corpora in the instance and the ontologies that were cognitive applied to each corpus.

## Step 2.  Discover potential criteria for searching literature
{: #type-ahead}
The second example calls the GET /v1/corpora/{corpus}/search/typeahead method and requests a JSON response.  The example requests ontology artifacts matching or containing the phrase 'seps'.
```
curl -X GET -u "apikey:{apikey}"{ \
--header "Accept: application/json" \
"{url}/v1/corpora/{corpus}/search/typeahead?version=2019-03-28&query=seps&ontologies=mesh&verbose=false&_limit=20&max_hit_count=5000000&no_duplicates=true"
```
{: pre}

The service returns a JSON object that lists the ontology artifacts found in the corpus that match or contain the original phrase and additional metadata including the semantic type, unique identifier, ontology source, and artifact prevalence in the corpus.

## Step 3.  Search the corpus
{: "search"}
The third example takes a suggested ontology artifact from step 2 and submits it as search criteria to retrieve a set of matching document identifiers calling the POST /v1/corpora/{corpus}/search method and requests a JSON response.

```
curl -X POST -u "apikey:{apikey}" \
--header "Content-Type: application/json" \
--header "Accept: application/json" \
-d "{
  "query": {
    "concepts": [
      {
        "ontology": "mesh",
        "id": "D018805",
        "rank": 10,
        "type": "Diseases",
        "includeRelated": [
          "children"
        ]
      }
    ]
  },
  "returns": {
    "documents": {
        "limit": "100",
        "offset": 0
    }
  }
}" "{url}/v1/corpora/{corpus}/search?version=2019-03-25&verbose=false"
```
{: pre}

The service returns a JSON object that identifies the total number of matching documents in the corpus and a list of 100 or the configured limit of results that specify the document id, title, originating corpus, and proposed links for next actions.

## Step 4.  Review results
{: "review-document"}
The fourth step takes a document identifier from step 3 and calls the GET /v1/corpora/{corpus}/documents/{document_id} method and requests a JSON response.
```
curl -X GET -u "apikey:{apikey}" \
--header "Accept: application/json" \
"{url}/v1/corpora/{corpus}/documents/{document_id}?version=2019-03-28&verbose=true"
```
{: pre}

The service returns a JSON object listing the metadata fields for the document and the text sections for the document.

## Next steps
{: "getting_started_next_steps"}
Learn more [advanced command invocations](/docs/services/wh-iml?topic=wh-iml-advanced-invocations).