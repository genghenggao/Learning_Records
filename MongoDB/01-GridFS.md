# GridFS

[TOC]

## 一、GridFS简介

- Instead of storing a file in a single document, GridFS divides the file into parts, or chunks [[1\]](https://docs.mongodb.com/manual/core/gridfs/#chunk-disambiguation), and stores each chunk as a separate document. By default, GridFS uses a default chunk size of 255 kB; that is, GridFS divides a file into chunks of 255 kB with the exception of the last chunk.  

- In MongoDB, use [GridFS](https://docs.mongodb.com/manual/reference/glossary/#term-gridfs) for storing files larger than 16 MB. 



参考： https://docs.mongodb.com/manual/core/gridfs/ 



## 二、HDFS与GridFS

- 如果需要对存储的数据进行更深层的分析和挖掘，使用HDFS优于GridFS；相反，如果进行时需要存储下来，然后就直接查询，也就是实时性较高的数据选在使用GridFS却比HDFS有着天然的优势（MongoDB高效的读取性能）。 

