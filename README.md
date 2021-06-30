# ecs-training-notes
Training notes from the ES master course from Udemy

ES uses a structure called inverted index
each unique word will be acting as a term and points to the documents in which the word appers
relevancy scores determines the search results
- inserting is called indexing in es
- table   : index
  row     : document
  column  : field
  Type*    : sub-division of an index. will be depricated.
- GET command returns the document as a response.
  GET /vehicles index will return the structure, es will implicitly configure the structure.
- HEAD returns 200 - OK or 404 - Not Found
- PUT command replaces and reindexes the document. documents are immutable
- POST with the update as below works the same as PUT
  Example: ```
    POST /vehicles/car/123/_update
    {
      "doc": {
        "driver": "Tom"
      }
    } ```
- DELETE marks the document as deletes. it also increments the version.
  ES daemon wipes out the marked documents regularly and then claims the disk space.
  1. DELETE /vehicles/car deletes the documents of type car
  2. DELETE /vehicles you can delete the index
- Components of an index:
  1. aliases - defines the alternate names for the index
  2. mappings - automatically maps the type of the fields 
        1. index can support only ONE type since version 6
            /employees/_doc/332 - here _doc is the type
        2. we can get rid of type since version 7
            /employees/332 is valid from version 7
        3. we can use discover tab in Kibana to see all the defined indexes
  3. settings - index settings such as shards, replicas etc.
  4. Basic query
        1. GET business/building/_search - endpoint to search the index. Not only gives the documents of that index, it also gives out took, shards/successful, hits            objects hits array which contains our actual documents
        2. From version 7 business/_search will be valid
 
 
