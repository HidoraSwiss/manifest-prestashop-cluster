# Highly Available and Auto-scalable Prestashop Cluster

A JPS package deploy Prestashop that initially contains 2 balancers, 2 application servers, 2 MySQL databases, 1 ProxySQL (load-balancing) and 1 storage container.

This manifest is based on the configuration of a [Wordpress cluster](https://github.com/jelastic-jps/wordpress-cluster) and the [Scalable Mysql Cluster](https://github.com/jelastic-jps/mysql-cluster/tree/master/mysql-cluster-orchestrator) made by Jelastic.

## Environment Topology
![Cluster Topology](images/topology.png)

### Specifics
| Layer | Server          | Number of CTs <br/> by default | Cloudlets per CT <br/> (reserved/dynamic) | Options |
| ----- | --------------- | :----------------------------: | :--------------------------------------: | :-----: |
| LB    | Nginx           |               2                |                   1/8                    |    -    |
| AS    | Nginx (PHP-FPM) |               2                |                   1/8                    |    -    |
| DB    | MySQL           |               2                |                   1/8                    |    -    |
| ST    | Shared Storage  |               1                |                   1/8                    |    -    |

* LB - Load balancer
* AS - Application server
* DB - Database
* ST - Shared Storage

**Prestashop Version**: 1.7 (see manifest for details)<br/>
**Nginx Version**: 1.10.1<br/>
**Php Version**: 7.0.10<br/>
**MySQL Database**: 5.7.14<br/>

### Additional functionality:
* MySQL databases in auto-scaled and load-balanced cluster;
* horizontal scaling enabled on compute nodes by CPU load. New AppServer will be added while 70% loading;

---

## Deployment

### Public Cloud

In order to get this solution instantly deployed, click the "Deploy" button, specify your email address within the widget, choose one of the [Jelastic Public Cloud providers](https://jelastic.cloud) and press Install.

[![Deploy](https://github.com/jelastic-jps/git-push-deploy/raw/master/images/deploy-to-jelastic.png)](https://jelastic.com/install-application/?manifest=https://raw.githubusercontent.comHidoraSwiss/manifest-prestashop/master/manifest.jps) 

### Private Cloud 
To deploy this package to Jelastic Private Cloud, import [this JPS manifest](../../raw/master/manifest.jps) within your dashboard ([detailed instruction](https://docs.jelastic.com/environment-export-import#import)).

### Add To Website
More information about installation widget for your website can be found in the [Jelastic JPS Application Package](https://github.com/jelastic-jps/jpswiki/wiki/Jelastic-JPS-Application-Package) reference.
