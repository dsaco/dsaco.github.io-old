---
layout: post
title:  "Mongodb操作"
date:   2019-05-29 16:13 +0800
tags: Mongodb
---

### Insert
##### Example
```
db.things.save(thing)
```
### Update
##### Operation
```
$set
$inc
```
##### Description
```
db.things.update(
    <query>, 
    <update>,
    upsert: <boolean>, //可选，这个参数的意思是，如果不存在update的记录，是否插入objNew,true为插入，默认是false，不插入。
    multi = <boolean>, //可选，mongodb 默认是false,只更新找到的第一条记录，如果这个参数为true,就把按条件查出来多条记录全部更新。
)
```
##### Example
```
db.things.update(
    { field: FIELD },
    { $set: { field2: FIELD2 } },
    false,
    true,
)
```
### Delete
### Search
##### Condition Operation
```
$gt : > 
$lt : < 
$gte: >= 
$lte: <= 
$ne : !=、<> 
$in : in 
$nin: not in 
$all: all 
$not: isn't
```
##### Example
```
db.things.find()
db.things.find({field: TITLE})
db.things.find().count()
db.things.find().limit(PAGESIZE)
db.things.find().skip(PAGESIZE * PAGENO)
db.things.find({field: { $gt: CREATED }}) > CREATED
db.things.find({field: { $lt: CREATED }}) < CREATED
db.things.find({field: { $gte: CREATED }}) >= CREATED
db.things.find({field: { $lte: CREATED }}) <= CREATED
db.things.find({field: { $gt: CREATED1, $lt: CREATED2 }})  CREATED1 < value < CREATED2
db.things.find({field: { $ne: TITLE }}) != TITLE
db.things.find({field: { $in: ARRAY }}) ARRAY.indexOf(field) !== -1
db.things.find({field: { $nin: ARRAY }}) ARRAY.indexOf(field) === -1
db.things.find({field: { $all: ARRAY }}) field all in ARRAY
db.things.find({field: { $size: SIZE }}) filed.length === SIZE
db.things.find({field: { $exists: BOOLEAN }}) exist field
db.things.find({'field.name': NAME})
db.things.find({field: { $not: RegExp }}) 

db.things.distinct("topic") all topics
db.person.distinct("friends", {"nickName" : {"$in" : ["Zhangsan", "Lisi"]}})
```
