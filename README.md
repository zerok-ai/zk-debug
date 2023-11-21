# Zk-debug
This pod acts a proxy for accessing redis and postgres on the client cluster.

# Setting up
For setup make sure you have the correct configuration in values.yaml. Especialy for redis and postgresUri.

Postgres uri is the base64 value of 'postgresql://username:password@hostname:5432/dbname'. The hostname will be kubernetes DNS in the format of 'svcname.namespace.' etc.

# Proxy for redis
Example requests:

PUT http://webdis-server:port/SET/myKey/123
GET http://webdis-server:port/GET/myKey
PUT http://webdis-server:port/HSET/myHash/field1/hello
GET http://webdis-server:port/HGET/myHash/field1

# Proxy for postgres
Examples:

1. To get full contents of a table.
GET http://your-postgrest-server:port/my_table 

2. Where condition with a column value equals a particular value
GET http://your-postgrest-server:port/my_table?column1=eq.value1 

3. Where condition with a column value is less than a particular value
GET http://your-postgrest-server:port/my_table?column1=lt.value1 

Refer this doc https://postgrest.org/en/stable/references/api.html for full API. 
