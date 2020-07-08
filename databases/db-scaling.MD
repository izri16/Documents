# DB Scaling

## CAP theorem
* C -> consistency (Every read receives the most recent write or an error)
* A -> availability (Every request receives a (non-error) response, without the guarantee that it contains the most recent write)
* P -> partition tolerance (The system continues to operate despite an arbitrary number of messages being dropped (or delayed) by the network between nodes)

The CAP theorem states you can have any two, but not all of those properties in distributed database. In reality you can not avoid P so you must choose between A and C.

# Postgresql scaling
Generaly relational database are easy to scale vertically (add more CPU/RAM/Storage), but hard to scale horizontaly (multiple instances).
For example Amazon RDS allows vertical scaling up to 64TB for postresql database with option to set read replicas (whole db copyied).
For storing even more data one would need to use NoSQL database that is easier to scale horizontally using sharding not just read replicas.
Relational databases are designed to scale up on expensive single machines.

## How amazon RDS handles Read replicates + (consistency vs availability)?
If you require "consistency" you should read from the "master" database, which is the only one you write into and which is always up to date.
If you care about "availability" (or do not care about "consistency") instead you should read from one of read replicas with will be eventually consistent, but not necessary consistent. The decision can be done on per query basis.
