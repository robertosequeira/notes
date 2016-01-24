# MongoDB

## Mint - Ubuntu

### Paths

| File      | Path                         |
|:---------:|------------------------------|
| Config    | /etc/mongod.conf             |
| Log       | /var/log/mongodb/mongod.log  |
| DB        | /var/lib/mongodb             |

### Service

```
sudo service mongod start
sudo service mongod stopt
sudo service mongod restart
```

## Import data

Download sample data from : http://media.mongodb.org/zips.json

```
mongoimport --db test --collection zips --drop --file zips.json 
```

## Ruby

Reference:
 - https://docs.mongodb.org/ecosystem/tutorial/ruby-driver-tutorial/

### irb

```
require 'mongo'
Mongo::Logger.logger.level = ::Logger::INFO
client = Mongo::Client.new('mongodb://localhost:27017')
client = db.use('test')
client.database.name
client.database.collection_names
client[:zips].find.first
```

### Create a connection

```
client = Mongo::Client.new([ '127.0.0.1:27017' ], :database => 'test')
client = Mongo::Client.new([ '127.0.0.1:27017' ], :database => 'test', :connect => :direct)
client = Mongo::Client.new('mongodb://127.0.0.1:27017/test')
```

### Insert

```
client[:artists].insert_one({ name: 'FKA Twigs' })
client[:artists].insert_many([
  { :name => 'Flying Lotus' },
  { :name => 'Aphex Twin' }
])
```

### Find

```
coll = client[:race]

coll
  .find(group: group)
  .projection(_id: 0, group: 0)
  .sort(secs: 1)
  .skip(offset)
  .limit(limit)
```
| Method           |        |
|:----------------:|--------|
| `find`           | Finds according to field/value |
| `projection`     | Excludes (`group: 0`) or includes (`first_name: 1`) a field in the query result |
| `sort`           | Sorts asc (`name: 1`) or desc (`name: -1`) by field |
