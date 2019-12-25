# Asclepius-database
Selecting a database module for Asclepius system was a bit challenging. Any way after reffering some documents regarding already available database solutions mySQL and postgresql was finalized to select one from two.
But considering following comparison it was decided to select postgresql .

https://www.guru99.com/postgresql-vs-mysql-difference.html

Then our focus was to run the postgresql in a docker to be easy deployment already docker deamon installed environment.
I followed following link for this perposes.

https://hackernoon.com/dont-install-postgres-docker-pull-postgres-bee20e200198

You may omit the volume creation if data persistance is not requried.

```
mkdir -p $HOME/docker/volumes/postgres

docker run --rm   --name pg-docker -e POSTGRES_PASSWORD=docker -d -p 5432:5432 -v $HOME/docker/volumes/postgres:/var/lib/postgresql/data  postgres


```

You can start clonning this project
```
git clone https://github.com/seewaveorg/Asclepeus-postgresql-db.git
```

Then move in to the project folder and start building using docker compose. Later Kubernetes will be introduced instead of kubernetes

```
docker build -t postgresql .
```


# CREATING A DATABASE CLUSTER

https://severalnines.com/database-blog/how-deploy-postgresql-docker-container-using-clustercontrol

Creating a cluster of Postgresql servers is the plan for Ausclepius project.

### Make all node ssh enabled
```
docker exec -ti node1 apt-get install -y openssh-server openssh-client
docker exec -ti node2 apt-get install -y openssh-server openssh-client



```

# ClusterControl

ClusterControl v1.7.4

2019-09-30

In this release we now support cluster to cluster replication for MySQL Galera and PostgreSQL clusters.
One primary use case is for disaster recovery by having a hot standby site/cluster which can take over when the main site/cluster has failed.
We also added support for MariaDB 10.4/Galera 4.x, ProxySQL 2.0 and managing database users for PostgreSQL clusters.

Let us know what you think about these features and changes anytime (Submit Feedback)
!

Feature Details
Cluster to Cluster Replication

    Asynchronous MySQL replication between MySQL Galera clusters.
    Streaming replication between PostgreSQL clusters.
    Clusters can be rebuilt with a backup or by streaming from a master cluster.

Misc

    MariaDB 10.4/Galera 4.x support.
    ProxySQL 2.0 support.
    Database User Management for PostgreSQL clusters.

ClusterControl v1.7.3

2019-06-28

In this release we have added support for running multiple PostgreSQL instances on the same server with improvements to PgBackRest to support those environments.
We have also added additional cluster types to our cloud deployment and support for scaling out cloud deployed clusters with automated instance creation. Deploy MySQL Replication, PostgreSQL, and TimeScaleDB clusters on AWS, GCE, and Azure.

Let us know what you think about these features and changes anytime (Submit Feedback)
!

Feature Details
PostgreSQL

    Manage multiple PostgreSQL instances on the same host.
    Improvements to pgBackRest with non-standard instance ports and custom stanzas.
    New Configuration Management page to manage your database configuration files.
    Added metrics to monitor Logical Replication clusters.

Cloud Integration

    Automatically launch a cloud instance and scale out your database cluster by adding a new DB node (Galera) or replication slave (Replication).
    Deploy following new replication database clusters:
        Oracle MySQL Server 8.0
        Percona Server 8.0
        MariaDB Server 10.3
        PostgreSQL 11.0 (Streaming Replication).
        TimescaleDB 11.0 (Streaming Replication).

Misc

    Backup verification jobs with xtrabackup can use the --use-memory parameter to limit the memory usage.
    A running backup verification server will show up in the Topology view as well.
    MongoDB sharded clusters can add/register an existing MongoDB configuration node.
    The clustercontrol-cmonapi (CMON API) package is deprecated from now on and no longer required.
    A few more legacy ExtJS pages have been migrated to AngularJS:
        Configuration Management for MySQL, MongoDB, and MySQL NDB Cluster.
        Email Notifications Settings.
        Performance->Transaction Logs.




