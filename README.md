# osm-to-sql

---

Simple OSM XML data to SQL converter command. This command will create 7 SQL files with foreign key constraints. You can use these SQL files with MySQL/ SQLite or any other SQL server.

## Usage

This is the default help menu for the command line tool.

```

Usage:
    osm-to-sql [OPTIONS] -i <xml_file_path.xml> -d <output_directory>

OPTIONS:
    -i        Input open street map file in XML format.
    -l        Default varchar length to using in table creation. [250]
    -d        Output directory to save output sql files.
    -r        Maximum rows per one SQL insert query. [400]
    -h        Prints help information

```

## Table mappings

All tables have foreign key constrations. And please import with the following order when you importing to your database server.

```
    1.nodes
        id,lat,lng,version,changeset,user,uid,visible,date_time

    2.ways
        id,version,changeset,user,uid,visible,date_time

    3.way_nodes
        way_id,node_id
            -- way_id = ways(id)
            -- node_id = nodes(id)

    4.relations
        id,version,changeset,user,uid,visible,date_time

    5.relation_members
        rm_id,relation_id,node_id,way_id,role
            -- relation_id = relations(id)
            -- node_id = nodes(id)
            -- way_id = ways(id)

    6.tags
        id,name

    7.ref_tags
        rt_id,tag_id,node_id,relation_id,way_id,value
            -- tag_id = tags(id)
            -- node_id = nodes(id)
            -- relation_id = relations(id)
            -- way_id = ways(id)
 
```

## Contirbutions

All contibutions and issued are welcome. Please help me to make this tool faster and powerfull.
