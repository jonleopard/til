# Enabling a PostgreSQL Extension

##### Connect to your database

If using a docker container, do something like:

`docker exec -it <containerID> bash`


##### Login to your postgres instance

Once insde your VM or container, login to your postgres instance:
`psql -U <dbAdminUsername>`



##### Viewing & Enabling Extensions

You can list the available extensions in your postgres instance by running
`\df` (describe functions). If the extension exists but you don't see it listed,
then you'll need to drop the extension and re-add it:


```
db=# \df
                       List of functions
 Schema | Name | Result data type | Argument data types | Type
--------+------+------------------+---------------------+------
(0 rows)
CREATE EXTENSION "uuid-ossp";
ERROR:  extension "uuid-ossp" already exists
DROP EXTENSION "uuid-ossp";
CREATE EXTENSION "uuid-ossp";
db=# \df
                                  List of functions
 Schema |        Name        | Result data type |    Argument data types    |  Type
--------+--------------------+------------------+---------------------------+--------
 public | uuid_generate_v1   | uuid             |                           | func
 public | uuid_generate_v1mc | uuid             |                           | func
 public | uuid_generate_v3   | uuid             | namespace uuid, name text | func
 public | uuid_generate_v4   | uuid             |                           | func
 public | uuid_generate_v5   | uuid             | namespace uuid, name text | func
 public | uuid_nil           | uuid             |                           | func
 public | uuid_ns_dns        | uuid             |                           | func
 public | uuid_ns_oid        | uuid             |                           | func
 public | uuid_ns_url        | uuid             |                           | func
 public | uuid_ns_x500       | uuid             |                           | func

db=# select uuid_generate_v4();
           uuid_generate_v4
--------------------------------------
 1c3a6827-0ac9-4fa3-8fb4-4ae6d699f257
(1 row)

```
