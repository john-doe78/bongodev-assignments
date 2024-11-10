### 1. How do you perform a join operation in MongoDB using `$lookup`?
```javascript
db.orders.aggregate([
  {
    $lookup: {
      from: "products",
      localField: "productId",
      foreignField: "_id",
      as: "product_details"
    }
  }
])
```
- a) Using `$match`
- b) Using `$lookup`
- c) Using `$merge`
- d) Using `$project`

**Answer**: b) Using `$lookup`

### 2. What is the difference between `$match` and `$project` in the aggregation pipeline?
- a) `$match` filters documents and `$project` reshapes them
- b) `$match` reshapes documents and `$project` filters them
- c) `$project` filters documents and `$match` reshapes them
- d) There is no difference

**Answer**: a) `$match` filters documents and `$project` reshapes them

### 3. What operator is used to perform a case-insensitive match in MongoDB?
```javascript
db.collection.find({ name: { $regex: "^mongodb$", $options: "i" } })
```
- a) `$matchInsensitive`
- b) `$caseInsensitive`
- c) `$regex` with `$options: "i"`
- d) `$text`

**Answer**: c) `$regex` with `$options: "i"`

### 4. How do you use the `$facet` operator in MongoDB?
```javascript
db.orders.aggregate([
  {
    $facet: {
      "category1": [{ $match: { category: "Electronics" } }],
      "category2": [{ $match: { category: "Clothing" } }]
    }
  }
])
```
- a) To sort results by category
- b) To perform multiple aggregation pipelines simultaneously
- c) To filter results based on categories
- d) To join collections

**Answer**: b) To perform multiple aggregation pipelines simultaneously

### 5. How do you implement pagination in MongoDB using `skip` and `limit`?
```javascript
db.collection.find().skip(20).limit(10)
```
- a) By using `$skip` and `$limit`
- b) By using `skip()` and `limit()` methods
- c) By using `$limit` only
- d) By using `$skip` only

**Answer**: b) By using `skip()` and `limit()` methods

### 6. How do you use the `$unwind` operator in MongoDB?
```javascript
db.orders.aggregate([
  { $unwind: "$items" }
])
```
- a) To group documents by a specific field
- b) To flatten an array field into multiple documents
- c) To filter an array based on a condition
- d) To merge two arrays

**Answer**: b) To flatten an array field into multiple documents

### 7. What does the `$group` operator do in an aggregation pipeline?
```javascript
db.orders.aggregate([
  { $group: { _id: "$category", totalAmount: { $sum: "$amount" } } }
])
```
- a) Groups documents by a specific field and applies an aggregation operation (e.g., sum, avg)
- b) Sorts documents by a specific field
- c) Filters documents based on a specific condition
- d) Reshapes documents to a new format

**Answer**: a) Groups documents by a specific field and applies an aggregation operation (e.g., sum, avg)

### 8. How do you create a compound index in MongoDB?
```javascript
db.collection.createIndex({ name: 1, age: -1 })
```
- a) db.collection.createIndex({ name: 1, age: -1 })
- b) db.collection.createIndex([{ name: 1 }, { age: -1 }])
- c) db.collection.createIndex({ "name.age": 1 })
- d) db.collection.createCompoundIndex({ name: 1, age: -1 })

**Answer**: a) db.collection.createIndex({ name: 1, age: -1 })

### 9. How do you use the `$addFields` operator in an aggregation pipeline?
```javascript
db.orders.aggregate([
  { $addFields: { totalPrice: { $multiply: ["$quantity", "$price"] } } }
])
```
- a) To add a new field to the output documents
- b) To remove fields from the output documents
- c) To sort the documents by a field
- d) To group the documents based on a field

**Answer**: a) To add a new field to the output documents

### 10. How do you perform a multi-field sort in MongoDB?
```javascript
db.collection.find().sort({ name: 1, age: -1 })
```
- a) Use the `$sort` operator with multiple fields
- b) Use the `sort()` method with multiple fields
- c) Use the `$multiSort` operator
- d) MongoDB doesn’t support multi-field sorting

**Answer**: b) Use the `sort()` method with multiple fields

### 11. How do you ensure that a field is unique in a MongoDB collection?
```javascript
db.collection.createIndex({ email: 1 }, { unique: true })
```
- a) By creating a primary key
- b) By creating a unique index
- c) By using `$unique` operator
- d) By using `$ensureUnique`

**Answer**: b) By creating a unique index

### 12. How do you perform a geospatial query in MongoDB?
```javascript
db.places.find({ location: { $near: { $geometry: { type: "Point", coordinates: [0, 0] }, $maxDistance: 5000 } } })
```
- a) By using `$geoNear`
- b) By using `$geoWithin`
- c) By using `$near` and `$geometry`
- d) By using `$geospatial`

**Answer**: c) By using `$near` and `$geometry`

### 13. What is the purpose of the `$merge` operator in MongoDB?
```javascript
db.orders.aggregate([
  { $group: { _id: "$category", totalAmount: { $sum: "$amount" } } },
  { $merge: { into: "category_totals" } }
])
```
- a) To join two collections together
- b) To save the aggregation result to a new collection
- c) To filter documents before saving them
- d) To delete the collection after the operation

**Answer**: b) To save the aggregation result to a new collection

### 14. How do you update multiple documents in MongoDB?
```javascript
db.collection.updateMany({ status: "pending" }, { $set: { status: "completed" } })
```
- a) Using `update()`
- b) Using `updateOne()`
- c) Using `updateMany()`
- d) Using `findAndModify()`

**Answer**: c) Using `updateMany()`

### 15. How do you find documents where a field value is within a specific range in MongoDB?
```javascript
db.collection.find({ age: { $gte: 18, $lte: 30 } })
```
- a) By using `$in`
- b) By using `$gte` and `$lte`
- c) By using `$range`
- d) By using `$between`

**Answer**: b) By using `$gte` and `$lte`

### 16. How do you perform a text search on a specific field in MongoDB?
```javascript
db.collection.createIndex({ description: "text" })
db.collection.find({ $text: { $search: "mongodb" } })
```
- a) By using the `$search` operator
- b) By creating a text index and using `$text`
- c) By using `$match` with a text operator
- d) MongoDB doesn’t support text search

**Answer**: b) By creating a text index and using `$text`

### 17. How do you use `$setWindowFields` in MongoDB for window functions?
```javascript
db.orders.aggregate([
  {
    $setWindowFields: {
      partitionBy: "$category",
      sortBy: { date: 1 },
      output: { cumulativeTotal: { $sum: "$amount" } }
    }
  }
])
```
- a) To calculate a running total for a grouped dataset
- b) To filter documents based on a condition
- c) To create a custom sort order
- d) To generate new documents based on calculations

**Answer**: a) To calculate a running total for a grouped dataset

### 18. How can you use `$count` to get the total number of documents in a collection?
```javascript
db.collection.aggregate([
  { $count: "total_documents" }
])
```
- a) By using the `count()` method
- b) By using the `$count` operator
- c) By using the `size()` method
- d) MongoDB doesn’t provide a counting feature

**Answer**: b) By using the `$count` operator

### 19. What is the purpose of the `$out` operator in MongoDB?
```javascript
db.orders.aggregate([
  { $group: {

 _id: "$category", totalAmount: { $sum: "$amount" } } },
  { $out: "category_totals" }
])
```
- a) To output the aggregation result to a new file
- b) To save the aggregation result to a collection
- c) To filter documents based on specific fields
- d) To display the aggregation result in the console

**Answer**: b) To save the aggregation result to a collection

### 20. How do you perform a range query on an embedded array field?
```javascript
db.collection.find({ "items.price": { $gte: 100, $lte: 500 } })
```
- a) By using `$arrayRange`
- b) By using `$gte` and `$lte` for array fields
- c) By using `$arraySize`
- d) By using `$in`

**Answer**: b) By using `$gte` and `$lte` for array fields

### 21. What does the `$push` operator do in MongoDB?
```javascript
db.collection.updateOne({ _id: 1 }, { $push: { items: "new_item" } })
```
- a) Adds a new element to the beginning of an array
- b) Adds a new element to the end of an array
- c) Removes an element from an array
- d) Creates a new array

**Answer**: b) Adds a new element to the end of an array

### 22. How do you remove a field from a document in MongoDB?
```javascript
db.collection.updateOne({ _id: 1 }, { $unset: { age: "" } })
```
- a) By using `$pull`
- b) By using `$unset`
- c) By using `$delete`
- d) By using `$remove`

**Answer**: b) By using `$unset`

### 23. What does the `$expr` operator allow you to do?
```javascript
db.collection.find({ $expr: { $gt: ["$price", "$cost"] } })
```
- a) To filter documents based on a computed expression
- b) To match documents using regular expressions
- c) To aggregate documents in a pipeline
- d) To evaluate JavaScript expressions in queries

**Answer**: a) To filter documents based on a computed expression

### 24. How do you perform a conditional update with the `$cond` operator?
```javascript
db.collection.updateMany(
  {},
  [{ $set: { status: { $cond: { if: { $gte: ["$age", 18] }, then: "adult", else: "minor" } } } }]
)
```
- a) By using `$if`
- b) By using `$cond`
- c) By using `$case`
- d) By using `$when`

**Answer**: b) By using `$cond`

### 25. What does the `$limit` operator do in an aggregation pipeline?
```javascript
db.collection.aggregate([
  { $limit: 10 }
])
```
- a) Limits the number of documents returned in the pipeline
- b) Limits the size of documents
- c) Limits the fields in documents
- d) Limits the number of fields in the query

**Answer**: a) Limits the number of documents returned in the pipeline

### 26. How do you perform a full-text search with MongoDB’s text index?
```javascript
db.collection.createIndex({ content: "text" })
db.collection.find({ $text: { $search: "database" } })
```
- a) By using `$search` operator
- b) By using `$fullText` operator
- c) By using `$text` operator
- d) MongoDB does not support full-text search

**Answer**: c) By using `$text` operator

### 27. How do you get the distinct values of a field in MongoDB?
```javascript
db.collection.distinct("category")
```
- a) By using `distinct()` method
- b) By using `$distinct` operator
- c) By using `$group` operator
- d) By using `find()` method with `$distinct`

**Answer**: a) By using `distinct()` method

### 28. How do you find documents that match any condition using `$or`?
```javascript
db.collection.find({ $or: [{ age: { $gte: 18 } }, { status: "active" }] })
```
- a) By using `$or` operator
- b) By using `$and` operator
- c) By using `$match` operator
- d) By using `$any` operator

**Answer**: a) By using `$or` operator

### 29. What is the purpose of the `$currentDate` operator?
```javascript
db.collection.updateOne({ _id: 1 }, { $currentDate: { lastModified: true } })
```
- a) Sets the current date as the value for a field
- b) Retrieves the current date from the system
- c) Adds a timestamp to a document when created
- d) Deletes a field if it contains a timestamp

**Answer**: a) Sets the current date as the value for a field

### 30. How do you use the `$arrayElemAt` operator to access array elements in MongoDB?
```javascript
db.collection.aggregate([
  { $project: { firstItem: { $arrayElemAt: ["$items", 0] } } }
])
```
- a) To filter array elements
- b) To access a specific element in an array by its index
- c) To modify elements in an array
- d) To join arrays from multiple collections

**Answer**: b) To access a specific element in an array by its index

### 31. How do you perform an update with a combination of operators in MongoDB?
```javascript
db.collection.updateOne({ _id: 1 }, { $inc: { age: 1 }, $set: { status: "active" } })
```
- a) By using `$update` operator
- b) By combining `$inc` and `$set` operators
- c) By using `$addToSet` operator
- d) By using `$combine` operator

**Answer**: b) By combining `$inc` and `$set` operators

### 32. How do you get the total count of documents in a MongoDB collection?
```javascript
db.collection.countDocuments()
```
- a) By using `count()` method
- b) By using `countDocuments()` method
- c) By using `aggregate()` with `$count`
- d) By using `$totalCount` operator

**Answer**: b) By using `countDocuments()` method

### 33. How do you handle null and missing values in MongoDB queries?
```javascript
db.collection.find({ field: { $eq: null } })
```
- a) By using `$missing` operator
- b) By using `$eq` with `null`
- c) By using `$isNull` operator
- d) MongoDB automatically ignores null values

**Answer**: b) By using `$eq` with `null`

### 34. How do you enable real-time analytics using MongoDB change streams?
```javascript
const changeStream = db.collection.watch();
changeStream.on("change", (change) => { console.log(change); });
```
- a) By using `watch()` method on a collection
- b) By using `realTime()` method on a collection
- c) By using `observe()` method on a collection
- d) By using `stream()` method on a collection

**Answer**: a) By using `watch()` method on a collection

### 35. How do you update only specific fields in a document without replacing the entire document?
```javascript
db.collection.updateOne({ _id: 1 }, { $set: { name: "John" } })
```
- a) By using `$set`
- b) By using `$replace`
- c) By using `$update` operator
- d) By using `$partialUpdate`

**Answer**: a) By using `$set`

### 36. What is the purpose of `$project` in aggregation pipelines?
```javascript
db.orders.aggregate([
  { $project: { name: 1, total: { $multiply: ["$quantity", "$price"] } } }
])
```
- a) To remove fields from documents
- b) To include or exclude fields in the output
- c) To group documents based on certain fields
- d) To sort the documents by a specific field

**Answer**: b) To include or exclude fields in the output

### 37. How do you create a time-to-live (TTL) index on a collection in MongoDB?
```javascript
db.collection.createIndex({ createdAt: 1 }, { expireAfterSeconds: 3600 })
```
- a) By using `$expire` operator
- b) By creating a TTL index with `expireAfterSeconds`
- c) By using `$ttl` operator
- d) MongoDB doesn’t support TTL indexes

**Answer**: b) By creating a TTL index with `expireAfterSeconds`

### 38. How do you perform a case-sensitive query using MongoDB’s `$regex` operator?
```javascript
db.collection.find({ name: { $regex: "^MongoDB$" } })
```
- a) By using `$regex` without any options
- b) By using `$regex` with `$options: "i"`
- c

) By using `$regex` with `$options: "s"`
- d) By using `$regex` with `$options: "c"`

**Answer**: a) By using `$regex` without any options

### 39. How do you aggregate values from multiple documents using `$sum` in MongoDB?
```javascript
db.orders.aggregate([
  { $group: { _id: "$category", totalAmount: { $sum: "$amount" } } }
])
```
- a) By using `$count` operator
- b) By using `$sum` operator
- c) By using `$add` operator
- d) By using `$aggregate` operator

**Answer**: b) By using `$sum` operator

### 40. What is the purpose of `$cond` in MongoDB aggregation?
```javascript
db.collection.aggregate([
  { $project: { status: { $cond: { if: { $gte: ["$age", 18] }, then: "adult", else: "minor" } } } }
])
```
- a) To calculate the sum of values
- b) To create a conditional expression
- c) To perform a group operation
- d) To modify documents based on field values

**Answer**: b) To create a conditional expression

### 41. How do you join two collections using `$lookup` in MongoDB?
```javascript
db.orders.aggregate([
  {
    $lookup: {
      from: "products",
      localField: "productId",
      foreignField: "_id",
      as: "productDetails"
    }
  }
])
```
- a) By using `$lookup` to join collections
- b) By using `$join` operator
- c) By using `$merge` operator
- d) By using `$combine` operator

**Answer**: a) By using `$lookup` to join collections

### 42. How do you perform an update on multiple fields conditionally in MongoDB?
```javascript
db.collection.updateMany(
  { age: { $gte: 18 } },
  [{ $set: { status: { $cond: { if: { $gte: ["$age", 18] }, then: "adult", else: "minor" } } } } }]
)
```
- a) By using `$set` and `$cond` together
- b) By using `$update` operator
- c) By using `$change` operator
- d) By using `$condition` operator

**Answer**: a) By using `$set` and `$cond` together

### 43. How do you implement pagination using the `skip` and `limit` operators in MongoDB?
```javascript
db.collection.find().skip(10).limit(20)
```
- a) By using `skip` and `limit` together
- b) By using `paginate()` method
- c) By using `$pagination` operator
- d) MongoDB doesn’t support pagination

**Answer**: a) By using `skip` and `limit` together

### 44. How do you use the `$arrayToObject` operator in MongoDB?
```javascript
db.collection.aggregate([
  { $project: { result: { $arrayToObject: [["key1", "value1"], ["key2", "value2"]] } } }
])
```
- a) To convert an array to an object
- b) To convert an object to an array
- c) To filter array elements
- d) To merge multiple objects into one

**Answer**: a) To convert an array to an object

### 45. How do you use `$push` to add elements to an array in MongoDB?
```javascript
db.collection.updateOne({ _id: 1 }, { $push: { items: "new_item" } })
```
- a) By using `$set`
- b) By using `$push`
- c) By using `$addToSet`
- d) By using `$append`

**Answer**: b) By using `$push`

### 46. How do you remove an element from an array in MongoDB?
```javascript
db.collection.updateOne({ _id: 1 }, { $pull: { items: "old_item" } })
```
- a) By using `$remove`
- b) By using `$pull`
- c) By using `$unset`
- d) By using `$delete`

**Answer**: b) By using `$pull`

### 47. How do you perform an aggregation operation that modifies existing fields in MongoDB?
```javascript
db.orders.aggregate([
  { $set: { totalPrice: { $multiply: ["$quantity", "$price"] } } }
])
```
- a) By using `$project`
- b) By using `$set`
- c) By using `$update`
- d) By using `$modify`

**Answer**: b) By using `$set`

### 48. How do you use `$min` and `$max` in an aggregation pipeline?
```javascript
db.orders.aggregate([
  { $group: { _id: "$category", minPrice: { $min: "$price" }, maxPrice: { $max: "$price" } } }
])
```
- a) To calculate the total sum of fields
- b) To calculate the average value of fields
- c) To find the minimum and maximum values of fields
- d) To group fields based on a condition

**Answer**: c) To find the minimum and maximum values of fields

### 49. How do you filter documents based on array elements in MongoDB?
```javascript
db.orders.find({ items: { $elemMatch: { price: { $gte: 100 } } } })
```
- a) By using `$arrayMatch`
- b) By using `$elemMatch`
- c) By using `$in`
- d) By using `$arrayElemAt`

**Answer**: b) By using `$elemMatch`

### 50. How do you perform a complex `$group` operation in MongoDB?
```javascript
db.orders.aggregate([
  { $group: { _id: "$category", totalAmount: { $sum: "$amount" }, totalItems: { $sum: 1 } } }
])
```
- a) By using `$combine`
- b) By using `$reduce`
- c) By using `$group`
- d) By using `$collect`

**Answer**: c) By using `$group`
```
