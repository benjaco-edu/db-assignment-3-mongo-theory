# Assignment 3

## Twitter data

see https://github.com/benjaco-edu/DB-Assignment-mongodb (i got feedback last time)

## Modeling

Model | Atomicity | Sharding |Indexes |Large Number of Collections | Collection Contains a Large Number of Small Documents
----|:----:|:----:|:----:|:----:|:----:
Arrays of Ancestors    |Atomicity is not a problem with insertions because an insert only touches one document, and no parent has to be updated, however it is if you would like to move a part of the tree to an other location| |The document has a rather flat structure which makes indexing easy|There is a lot of references to other documents, so it should be kept in the same collection| |
Materialized paths  | |This type of data structure can be sharded because of its flat structure but isn't good for it, some queries are going to be slow when multiple parts of the tree are spread over multiple shards||Same as above|This structure will contain a large number of small documents, which makes sharding effective|
Nested sets            |nested sets are a catastrophe for atomicity, each and every item has to be updated in the tree at modified, and if just 1 update goes wrong, the whole tree is destroyed|it is wonderful for sharding, left can be used as a shard key, and the related objects will likely be stored together|it is good for indexing as well, left and right can be indexed, and a lookup will take no time|| |
