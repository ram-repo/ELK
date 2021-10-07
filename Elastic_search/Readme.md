## Elastic search 
```
Elasticsearch is a NoSQL database which is based on Lucene search engine and is built with RESTful APIs. It is a highly flexible and distributed search and analytics engine. Also, it provides simple deployment, maximum reliability, and easy management through horizontal scalability. It provides advanced queries to perform detailed analysis and stores all the data centrally for quick search of the documents. 
```
## file format 
* Open an existing file with a .es file extenion or open a new text file (ctrl+n) and change the language mode to Elasticsearch (es) by pressing ctrl+k,m and select es. Elasticsearch queries and funtionalities are enabled in the es language mode in Visual Studio Code editor.

## When you work with Elasticsearch there are three major steps which you need to follow:

* Indexing
* Mapping
* Searching

### Indexing:
* Indexing is the process of adding the data Elasticsearch. It is called ‘indexing’ because when the data is entered into Elasticsearch, it gets placed into Apache Lucene indexes.  Elasticsearch then uses these Lucene indexes to store and retrieve the data. Indexing is similar to the create and update process of CRUD operations.

* An index scheme consists of name/type/id, where name and type are mandatory fields. In case you do not provide any ID, Elasticsearch will provide an id on its own. This entire query is then is appended to an HTTP PUT request and the final URL looks like:PUT name/type/id Along with the HTTP payload a JSON document, which contains the fields and values, is sent as well.

#### Example :
```
PUT /customer/_doc/1
{
 "ID" : 101,
 "FName" : "James",
 "LName" : "Butt",
 "Email" : "jbutt@gmail.com",
 "City" : "New Orleans",
 "Type" : "VIP"
}

Out Put :
#! Elasticsearch built-in security features are not enabled. Without authentication, your cluster could be accessible to anyone. See https://www.elastic.co/guide/en/elasticsearch/reference/7.14/security-minimal-setup.html to enable security.
{
  "_index" : "customer",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 1,
  "result" : "created",
  "_shards" : {
    "total" : 2,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 0,
  "_primary_term" : 1
}

## any Change and run again will get update version
#! Elasticsearch built-in security features are not enabled. Without authentication, your cluster could be accessible to anyone. See https://www.elastic.co/guide/en/elasticsearch/reference/7.14/security-minimal-setup.html to enable security.
{
  "_index" : "customer",
  "_type" : "_doc",
  "_id" : "1",
  "_version" : 2,
  "result" : "updated",  ## status update and Version also Changed
  "_shards" : {
    "total" : 2,
    "successful" : 1,
    "failed" : 0
  },
  "_seq_no" : 1,
  "_primary_term" : 1
}



```
