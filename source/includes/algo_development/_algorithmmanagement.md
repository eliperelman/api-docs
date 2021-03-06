# Algorithm Management

Using the Algorithmia API, you can create, publish, update, and inspect individual algorithms. At present, only our Python client supports algorithm management, and we've provided cURL examples for those algorithm management endpoints which our Python client does not yet support.

To try out a complete training-to-deployment pipeline, get the [runnable Jupyter Notebook](https://github.com/algorithmiaio/model-deployment).

IMPORTANT:

1. Before using these functions, update to the latest Python client: `pip install -U Algorithmia`

2. Create a *NEW* API Key at https://algorithmia.com/user#credentials or in your own Algorithmia cluster, with the option "Allow this key to manage my algorithms" turned on. Do not use this key for other purposes.  

## Create an Algorithm

```python
client=Algorithmia.client('API_KEY')
algo = client.algo('demo/Hello')
algo.create(
    details = {
        "label": "Hello World",
    },
    settings = {
        "language": "python3-1",
        "source_visibility": "closed",
        "license": "apl",
        "network_access": "full",
        "pipeline_enabled": True,
        "environment": "cpu"
    }
)
```

```javascript
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```shell
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```cli
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```r
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```ruby
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```java
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```scala
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```rust
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```nodejs
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```php
<?
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
?>
```

First, define an algo using `client.algo('USERNAME/ALGONAME')`, making sure that "USERNAME/ALGONAME" is *not* the name of an existing Algorithm.

Then, call `algo.create(details, settings)` -- the parameters are dictionaries with the following keys:

*details:*

- "label": "\<string>" #user-readable name of the algorithm
- "tagline": "\<string>" #(optional) one-liner summarizing the Algorithm's purpose
- "summary": "\<string>" #(optional)markdown describing the Algorithm, for the "docs" tab

*settings:*

- "language": "\<string>" #java, javascript, python2-langpack, python3-1, r, ruby, rust, scala
- "source_visibility": "\<string>" #open, closed
- "license": "\<string>" #apl, apache2, gpl3, mit
- "network_access": "\<string>" #isolated, full
- "pipeline_enabled": \<boolean> #can this algo call other algos?
- "environment": "\<string>" #cpu, gpu
- "royalty_microcredits": \<integer> #(optional) 0 for none
</pre>

Once this has been done, your algorithm will be visible at https://algorithmia.com/algorithms/USERNAME/ALGONAME ... but it doesn't have any code yet. You'll need to `git clone https://git.algorithmia.com/git/USERNAME/ALGONAME.git`, then add and commit code, before continuing on to the Publishing step.

## Update an Algorithm

```python
algo.update(
    details = {
        "label": "Echo", #user-readable name of the algorithm
    },
    settings = {
        "source_visibility": "open",
        "license": "apl",
        "network_access": "full",
        "pipeline_enabled": True,
        "environment": "cpu"
    }
)
```

```javascript
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```shell
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```cli
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```r
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```ruby
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```java
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```scala
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```rust
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```nodejs
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```php
<?
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
?>
```

If you need to change an Algorithm's settings after it cas been created, this can be done with a call to `algo.update(details, settings)` which takes these parameters:

*details:*

- "label": "\<string>" #user-readable name of the algorithm
- "tagline": "\<string>" #(optional) one-liner summarizing the Algorithm's purpose
- "summary": "\<string>" #(optional) markdown describing the Algorithm, for the "docs" tab

*settings:*

- "source_visibility": "\<string>" #open, closed
- "license": "\<string>" #apl, apache2, gpl3, mit
- "network_access": "\<string>" #isolated, full
- "pipeline_enabled": \<boolean> #can this algo call other algos?
- "environment": "\<string>" #cpu, gpu

## Delete Algorithm

`DELETE https://api.algorithmia.com/v1/algorithms/:owner/:algoname`

```shell
curl -X DELETE -H 'Authorization: Simple API_KEY' \
    https://api.algorithmia.com/v1/algorithms/demo/Hello
```

```cli
  # This client does not currently support deleting algorithms.
  # Please use cURL instead.
```

```python
  # This client does not currently support deleting algorithms.
  # Please use cURL instead.
```

```javascript
  // This client does not currently support deleting algorithms.
  // Please use cURL instead.
```

```r
  # This client does not currently support deleting algorithms.
  # Please use cURL instead.
```

```ruby
  # This client does not currently support deleting algorithms.
  # Please use cURL instead.
```

```java
  // This client does not currently support deleting algorithms.
  // Please use cURL instead.
```

```scala
  // This client does not currently support deleting algorithms.
  // Please use cURL instead.
```

```rust
  // This client does not currently support deleting algorithms.
  // Please use cURL instead.
```

```nodejs
  // This client does not currently support deleting algorithms.
  // Please use cURL instead.
```

```php
<?
  // This client does not currently support deleting algorithms.
  // Please use cURL instead.
?>
```

##### Path Parameters

Parameter | Description
--------- | -----------
owner | string, owner identifier
algoname | string, algorithm identifier

##### HTTP Response

A success response returns an HTTP 204 status code.

## Recompile your Algorithm

```python
algo.compile()
```

```javascript
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```shell
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```cli
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```r
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```ruby
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```java
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```scala
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```rust
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```nodejs
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```php
<?
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
?>
```

Any `git push` to your Algorithm's repo implicitly causes a compile to run on Algorithmia's servers. However, you can also manually force a compile if desired, using `algo.compile()`

## Get List of Algorithm Commits

`GET https://api.algorithmia.com/v1/algorithms/:owner/:algoname/log`

```javascript
  // This client does not currently support listing Algorithm commits.
  // Please use cURL instead.
```

```shell
curl -H 'Authorization: Simple API_KEY' \
    https://api.algorithmia.com/v1/algorithms/demo/Hello/log
```

```cli
  # This client does not currently support listing Algorithm commits.
  # Please use cURL instead.
```

```python
  # This client does not currently support listing Algorithm commits.
  # Please use cURL instead.
```

```r
  # This client does not currently support listing Algorithm commits.
  # Please use cURL instead.
```

```ruby
  # This client does not currently support listing Algorithm commits.
  # Please use cURL instead.
```

```java
  // This client does not currently support listing Algorithm commits.
  // Please use cURL instead.
```

```scala
  // This client does not currently support listing Algorithm commits.
  // Please use cURL instead.
```

```rust
  // This client does not currently support listing Algorithm commits.
  // Please use cURL instead.
```

```nodejs
  // This client does not currently support listing Algorithm commits.
  // Please use cURL instead.
```

```php
<?
  // This client does not currently support listing Algorithm commits.
  // Please use cURL instead.
?>
```

##### Path Parameters

Parameter | Description
--------- | -----------
owner | string, owner identifier
algoname | string, algorithm identifier

##### Query Parameters

Parameter | Description
--------- | -----------
since | string, The first commit SHA to list in the commits. This is included in the result list.
until | string, The last commit SHA to list in the commits. This is included in the result list.

##### HTTP Response

The response JSON contains an array of objects with the following attributes:

Attribute | Description
----------|------------
id | string, the commit SHA
short_message | string, truncated version of the commit message
message | string, full version of the commit message
author | string, author of the commit

## Get List of Algorithm Builds

`GET https://api.algorithmia.com/v1/algorithms/:owner/:algoname/builds/:build_id`

```javascript
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```shell
curl -H 'Authorization: Simple API_KEY' \
    https://api.algorithmia.com/v1/algorithms/demo/Hello/builds
```

```cli
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```python
  # This client does not currently support Algorithm Builds.
  # Please use cURL instead.
```

```r
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```ruby
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```java
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```scala
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```rust
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```nodejs
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```php
<?
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
?>
```

##### Query Parameters

Parameter | Description
--------- | -----------
marker | [Optional] Indicates the page of results to return. Only valid when using markers previously returned by this API. If omitted, then the first page is returned
limit | [Optional] The number of builds to return. Defaults to 10, if omitted.

##### HTTP Response

The response JSON contains the following attributes:

Attribute | Description
----------|------------
results | array of builds
marker | [Optional] string, indicates that there are more builds of this algorithm that can be queried for using the `marker` query parameter 
next_link | [Optional] string, hyperlink to next page of results

##### Build Object

A single build in the array of _builds_ contains:

Attribute | Description
----------|------------
build_id | string, an opaque build identifier
status | string, enum, one of: `in-progress`, `succeeded`, `failed`
commit_sha | string, version-controlled revision of the algorithm that was built
started_at | string, date-time, ISO-8601 timestamp of when the build started
finished_at | [Optional] string, date-time, ISO-8601 timestamp of when the build finished if it has a _completed_ status such as `succeeded` or `failed`; otherwise null.
resource_type | [Optional] string, always "algorithm_build"

## Get Algorithm Build

`GET https://api.algorithmia.com/v1/algorithms/:owner/:algoname/builds/:build_id`

```javascript
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```shell
curl -H 'Authorization: Simple API_KEY' \
    https://api.algorithmia.com/v1/algorithms/demo/Hello/builds/b57ee29b-31dd-4252-839d-edcb7e0c0ae3
```

```cli
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```python
  # This client does not currently support Algorithm Builds.
  # Please use cURL instead.
```

```r
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```ruby
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```java
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```scala
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```rust
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```nodejs
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```php
<?
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
?>
```

##### Path Parameters

Parameter | Description
--------- | -----------
build_id | string, build identifier

##### HTTP Response

The response JSON contains the following attributes:

Attribute | Description
----------|------------
build_id | string, an opaque build identifier
status | string, enum, one of: `in-progress`, `succeeded`, `failed`
commit_sha | string, version-controlled revision of the algorithm that was built
started_at | string, date-time, ISO-8601 timestamp of when the build started
finished_at | [Optional] string, date-time, ISO-8601 timestamp of when the build finished if it has a _completed_ status such as `succeeded` or `failed`; otherwise null.
resource_type | [Optional] string, always "algorithm_build"

## Get Algorithm Build Logs

`GET https://api.algorithmia.com/v1/algorithms/:owner/:algoname/builds/:build_id/logs`

```javascript
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```shell
curl -H 'Authorization: Simple API_KEY' \
    https://api.algorithmia.com/v1/algorithms/demo/Hello/builds/b57ee29b-31dd-4252-839d-edcb7e0c0ae3/logs
```

```cli
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```python
  # This client does not currently support Algorithm Builds.
  # Please use cURL instead.
```

```r
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```ruby
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```java
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```scala
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```rust
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```nodejs
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
```

```php
<?
  // This client does not currently support Algorithm Builds.
  // Please use cURL instead.
?>
```

##### Path Parameters

Parameters | Description
-----------|------------
build_id | string, build identifier

##### HTTP Response

The response JSON contains the following:

Attribute | Description
----------|------------
logs | string, a set of newline separated logs that were output during a build. Note, these logs may be large in size.

## Publish an Algorithm

```python
algo.publish(
    version_info = {
        "sample_input": "world"
    }
)
```

```javascript
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```shell
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```cli
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```r
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```ruby
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```java
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```scala
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```rust
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```nodejs
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```php
<?
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
?>
```

Once you've committed code, you can use `algo.publish(details, settings, version_info)` to make the Algorithm callable. All parameters are optional, and will overwrite those specified in the initial create() call if they conflict.

Note the addition of "algorithm_callability" to the settings parameter: if this is set to "public", your Algorithm will be published publicly, allowing any registered user to call it.

Under version_info, even if your sample_input is a dictionary, it must be encapsulated as a string, such as `"sample_input": "{\"text\": \"This is a very positive review for the movie. I absolutely loved it!\"}"`

*details:*

- "summary": "\<string>" #markdown describing the Algorithm, for the "docs" tab
- "tagline": "\<string>" #one-liner summarizing the Algorithm's purpose

*settings:*

- "algorithm_callability": "\<string>" #private, public
- "source_visibility": "\<string>" #open, closed
- "license": "\<string>" #apl, apache2, gpl3, mit
- "royalty_microcredits": \<integer> #0 for none

*version_info:*

- "sample_input": "\<string>" #example input visible to end-user

## Get info about an an Algorithm

```python
algo.info() #optional params: algo_hash
```

```javascript
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```shell
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```cli
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```r
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```ruby
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```java
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```scala
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```rust
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```nodejs
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```php
<?
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
?>
```

To inspect a previously created Algorithm, call `algo.info()` on it to obtain details similar to those specified at create(), as well as additional info such as the hash value of the latest compile (available in version_info.git_hash only if code has been pushed) or the last published version number (version_info.semantic_version only if it has been published).

## List Versions of an Algorithm

```python
algo.versions() #optional params: limit (<int>), marker (<string>), published (<boolean>), callable (<boolean>)
```

```javascript
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```shell
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```cli
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```r
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```ruby
  # This client does not currently support Algorithm Management.
  # Use Python or the OpenAPI spec instead:
  # https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```java
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```scala
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```rust
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```nodejs
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
```

```php
<?
  // This client does not currently support Algorithm Management.
  // Use Python or the OpenAPI spec instead:
  // https://algorithmia.com/developers/algorithm-development/algorithm-management
?>
```

To get info about every individual published version of your Algorithm, use `algo.versions()`

## Get Algorithm Repository Host Connection Status

If your algorithm's source code is hosted on a platform like GitHub, you can use this endpoint to determine if Algorithmia is still able to properly communicate with the repository host and fetch source code.

`GET https://api.algorithmia.com/v1/algorithms/:owner/:algoname/scm/status`

```javascript
  // This client does not currently support getting Algorithm repository host connection status.
  // Please use cURL instead.
```

```shell
curl -H 'Authorization: Simple API_KEY' \
    https://api.algorithmia.com/v1/algorithms/demo/Hello/scm/status
```

```cli
  # This client does not currently support getting Algorithm repository host connection status.
  # Please use cURL instead.
```

```python
  # This client does not currently support getting Algorithm repository host connection status.
  # Please use cURL instead.
```

```r
  # This client does not currently support getting Algorithm repository host connection status.
  # Please use cURL instead.
```

```ruby
  # This client does not currently support getting Algorithm repository host connection status.
  # Please use cURL instead.
```

```java
  // This client does not currently support getting Algorithm repository host connection status.
  // Please use cURL instead.
```

```scala
  // This client does not currently support getting Algorithm repository host connection status.
  // Please use cURL instead.
```

```rust
  // This client does not currently support getting Algorithm repository host connection status.
  // Please use cURL instead.
```

```nodejs
  // This client does not currently support getting Algorithm repository host connection status.
  // Please use cURL instead.
```

```php
<?
  // This client does not currently support getting Algorithm repository host connection status.
  // Please use cURL instead.
?>
```

##### Path Parameters

Parameter | Description
--------- | -----------
owner | string, owner identifier
algoname | string, algorithm identifier

##### HTTP Response

The response JSON contains the following attributes:

Attribute | Description
----------|------------
scm_connection_status | string, enum, one of: `active`, `deploy_key_error`, `provider_internal_error`
repository_public_deploy_key | [Optional] string
repository_webhook_secret | [Optional] string
repository_webhook_url | [Optional] string
