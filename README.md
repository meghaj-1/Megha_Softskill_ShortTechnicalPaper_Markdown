# Full Text Search
## What is full text search?
Full text search is avant-garde way to search a database. Full text search speedily finds all instances of a term (word) in a table without scaning rows and without knowing which column a term is stored in. Full text search works by using text indices. A text index stores positional information for all terms found in the columns you create the text index on.
[Reference.1.](http://infocenter.sybase.com/help/index.jsp?topic=/com.sybase.help.sqlanywhere.12.0.1/dbusage/full-text-search-what-is-it.html)

![](https://developers.foxitsoftware.com/wp-content/uploads/2019/04/full-text-search-document-management-workflow-1024x531.png "Full Text search Workflow")

3 types of full-text searches:
* Natural language search : as a phrase in natural human language (free text).
* Boolean search : search string contains the words to search for with operators for specific search requirements.
* Query expansion search : modification of a natural language search. First natural language search is performed and then result of this is processed by second part of query which returns rows from the second search. [Reference.2.](https://dev.mysql.com/doc/refman/8.0/en/fulltext-search.html#function_match)
  
  `Code` example:MATCH (col1,col2,...) AGAINST (expr [search_modifier])
  ```MySQL
  search_modifier:
  {
       IN NATURAL LANGUAGE MODE
     | IN NATURAL LANGUAGE MODE WITH QUERY EXPANSION
     | IN BOOLEAN MODE
     | WITH QUERY EXPANSION
  }
    ```
   
 
    After column addition to a full-text index, users and applications can run full-text queries over the text in the columns. These queries can search:

    * One/many specific words/phrases (simple term).
    * A word/phrase where the words begin with specified text (prefix term).
    * A word/phrase close to another word/phrase (proximity term).
    * Synonym of a certain word (thesaurus).
    * Words/phrases having weightage (weighted term).
    * Full-text queries are not case-sensitive, "Aluminum" or "aluminum" returns the same results.
[Reference.3.](https://docs.microsoft.com/en-us/sql/relational-databases/search/full-text-search?view=sql-server-ver15)

## Why Full Text Search Queries Are So Slow

Full text search doesn’t fit well in query plans. If a query is quite simple yet searching for an unusual keyword/(s), then full text search performs well. However,when query becomes complex, like more filtering is to be done on other tables, AND the more common your search keywords are, full text performance degrades.  [Reference.4.](https://www.brentozar.com/archive/2020/11/why-full-texts-contains-queries-are-so-slow)


## ElasticSearch
Elasticsearch is a distributed document-oriented search engine, which is used to store data in the form of a document.
### Advantages
- Compatible to run on every platform (developed in Java).
- Real-time search engine, document added just one second before is searchable.
- Offers gateway, allows creating full backups easily.
- Distributed document-oriented, easy to scale up in big organization.
- Multi-tenancy can be easily handled in Elasticsearch in comparison to Apache Solr.
- Documentation available in multiple languages.
- Open-source.
- Supports all document types except which do not support text rendering.

### Disadvantages
- Problem of split-brain occurs sometimes.
- Unlike Apache Solr, Elasticsearch does not posses multi-lingual support for handling request and response data.
- Not a good data store like other options (MongoDB, Hadoop, etc.)
- Chokes/looses data in case of streaming of TB's data per day.
- Not as simplest as out the box search to learn.

## Solr
Apache Solr is a subproject of Apache Lucene, which is the indexing technology behind most recently created search and index technology Solr is a search engine and a NoSQL database with transactional support. It is a document database that offers SQL support and executes it in a distributed manner.
### Advantages
- Flexible and powerful query language.
- High-speed response query.
- Nice documentation
- Good community support.
- Cluster mode with separate master and slave, easy to scale each type base when needed to increase input data or response speed.
### Disadvantages
- No authentication & no authorization, required to place inside a private network.
- Working with Solr cloud require additional Zookeeper.
- Master node requires reconfiguration if it goes down anytime.

## Lucene
Apache Lucene™ is a full-featured & high-performance text search engine library completely written in Java. It is a technology suitable for nearly any application that requires full-text search, especially cross-platform.
### Advantages
- Quickly searching huge amounts of data on a single machine instance.
- Extreme memory and disk efficient performance.
- Easy setup and integration into external systems.
- User interface for setup and maintenance.
- Easy cloud/cluster setup.
- Better, centralized documentation.
### Disadvantages
- Having scalability issues.
- Performance degrades with increasing large index size.

## Conclusion
Each of those search techniques have their own caveats and each of them might be suited for different purposes. Based on above facts Elasticsearch seems to be better choice as it has better documentation available and poses better inherent scalablity which is our primary goal to improve performance and scalability.

