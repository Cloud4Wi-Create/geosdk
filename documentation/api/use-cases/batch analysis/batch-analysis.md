# Batch Analysis

## Intro

Functionality to request batch analysis of various types and receive results through files

The functionality is designed to:

* Allow analysis on a large amount of data
* Allow analysis on hstorical data no longer available from the standard API endpoints
* Allow complex analysis not directly provided by any standard API endpoint
* Allow very large inputs by files (useful if an analysis involves thousands of points of interests)
* Allow setting hooks to be notified when the analysis finishes

## API overview

### Steps

1. Create an Analysis
2. (optional) Upload input files
3. Submit analysis
4. (Optional) Check the status of the analysis
5. Download the results

> If an hook is set, then a notification will be sent to that hook as soon as the analysis is completed

### Analysis lifecycle

* possible statuses: `waitingForInput`, `submittable`, `starting`, `running`, `succedeed`, `failed`

1. analysis created -> `waitingForInput` (`submittable` if no input file is expected)
2. input uploaded -> `submittable`
3. analysis submitted -> `starting`
4. the platform starts the analysis -> `running` 
5. the analysis terminates 
	1. correctly -> `succedeed` 
	1. with error -> `failed`


### Upload Input files

Allows to upload the input files for a specific analysis.
Each file must encode a Segment of a specific Dimension, according to what defined in the `inputFiles` field.
How the Segment is encoded in the file depends on the specific Dimension and format type.

**Endpoint:** `POST /analysis/:id/files/:identifier`

**PATH Parameters** 

* **`id`:** the ID of the analysis
* **`identifier`:** the identifier of the input file. It must be equal to the `identifier` of one of the elements in the `inputFiles`  array

**Headers**
* **Content-type:** `multipart/form-data`

**Supported File Encodings**: UTF-8


### Submit an analysis

Inform Geouniq analytics platform that the analysis can be executed.
The API will return a 409 invalid operation if some input file is missing.
The Staus of the analysis will change in `starting` and then in `running`.

**Endpoint:** `POST /analysis/:id/submit`

**Request Body**: No body expected

**Response Body**: The Analysis resource


### List analysis

Allows to get all the analysis of a given User

**Endpoint:** `GET /analysis`

**Response Body**: [Paginated response](https://gitlab.com/geouniq/documentation/blob/master/api/general-aspects/pagination.md). Each `item` is an Analysis resource

```json
{
	"items": [{<Analysis>}],
	"paging": {<Paging>}
}
```

### Read a specific analysis

Allows to get a specific analysis. Useful to check the status

**Endpoint:** `GET /analysis/:id`

**Response Body**: The Analysis resource

### Download results

Allows to get the results of a specific analysis.
Results are provided as a unique file, a `tar` **archive** (`.tar`). Such file contains the results of the analysis in various `csv` files zipped using `gzip` (`.csv.gz`). Directories are organized depending on job types, but in general results are organized as:
`<type-of-the-analysis>/<job-identifier>/results-partXXX.csv.gz`

As an example, the result of an analysis of type selection with three jobs (one, two, three) will result in a `.tar.gz` file composed as follows:
```
analysis_results_<analysisID>.tar:

selection
    |
    |- one
    |   |- selection-part0.csv.gz
    |   | ...
    |   |- selection-part100.csv.gz
    |
    |- two
    |   |- selection-part0.csv.gz
    |   | ...
    |   |- selection-part100.csv.gz
    |
    |- three
    |   |- selection-part0.csv.gz
    |   | ...
    |   |- selection-part100.csv.gz

```

**Endpoint:** `GET /analysis/:id/results`

**Response**:
	* `Content-type: application/gzip`

### Deleting an Analysis

**Endpoint:** `DELETE /analysis/:id`

### Receiving a Web Hook

When a Web Hook is configured for an analysis, an HTTP request will be sent as soon as the analysis completes.

The details of the request are as follows:

**METHOD:** `POST`

**HEADERS**
* `Content-type: application/json`

**BODY**

```json
{
  "analysisID": "AnalysisX",
  "status": "succeeded"
}
```

When the request is received, the status of the analysis can be succeeded or failed.
The analysisID can be used to get the results from [the related endpoint](#download_results)




