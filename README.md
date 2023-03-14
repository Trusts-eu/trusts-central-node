# TRUSTS Central Node

This repository contains deployment scripts for deploying a central node of the TRUSTS platform.

This deployment consists of a customized [IDS Metadata Broker](https://github.com/International-Data-Spaces-Association/metadata-broker-open-core) and its corresponding Apache Jena Fuseki instance. The modifications in this fork of the Metadata Broker are to accomodate a couple of extra SPARQL queries that were not supported in the original, and which are necessary for an efficient functioning of the TRUSTS platform. Some special configuration needed to launch the TRUSTS pltaform's Central Node is also included.

## To run
1. Clone this repository
2. Create at the root of this repository, a directory called `cert`. 
3. In the `./cert/` directory add: 
  *  The p12 file of your central node certificate. This should have been issued by the certificate authority of your TRUSTS deployment.
  *  A jks file corresponding to the same p12 file
  * The SSL certificate for the domain in which you will be deploying the central node, called `server.crt` and `server.key`
4. Create a file called `trustshosts` which contains domain name <-> IP mappings for any machines in your TRUSTS platfrom whose names are not in the public DNS. This file follows the format used by a unix `/etc/hosts` file. **This file must also contain an entry for the `broker-core` domain name, corresponding to the IP address of the deployment.**
5. Launch with `docker compose up`

Optionally, you can launch usint `docker compose -f docker-compose-dsc.yml up` which will also deploy a [Dataspace Connector](https://github.com/International-Data-Spaces-Association/DataspaceConnector) instance configured to enable this central node to distribute and synchronize RDF vocabularies generated using [PoolParty Semantic Suite](https://www.poolparty.biz/) as IDS Resources.



## Contributors

The main contributors to this code are:
* Nikos Fourlataras (Relational Greece) 
* Sotiris Karampatakis (Semantic Web Company)
* Victor Mireles (Semantic Web Company) 


## Funding
This code was created as part of project TRUSTS: Trusted secure data sharing space.

This project has received funding from the European Union's Horizon 2020 research and innovation programme under grant agreement [No 871481](https://cordis.europa.eu/project/id/871481).



