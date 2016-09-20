# Eclipse RDF4J

## Introduction

This is the Docker repository for RDF4J Server (which is RDF database server and the SPARQL endpoint service) and RDF4J Workbench (which is the Web UI of RDF4J Server for database and data management tasks). Eclipse RDF4J is the official successor to the OpenRDF Sesame framework. For more information about RDF4J, please refer to [Eclipse RDF4J Official Website](http://rdf4j.org/).

RDF4J is currently released with two version series 2.x and 1.x, where 2.x is the successor of Sesame 4.1 requiring Java 8 Runtime Environment and 1.x is the corresponding Java 7 backport. Accordingly, this Docker repository also includes both versions, with supported tags and Dockerfiles listed as follows:
* `2.0.1`, `2`, `latest`: Built with JRE 8 and Tomcat 8.5 [Dockerfile](https://github.com/yyz1989/docker-rdf4j/blob/master/2/2.0.1/Dockerfile)
* `1.0.1`, `1`: Built with JRE 7 and Tomcat 8 [Dockerfile](https://github.com/yyz1989/docker-rdf4j/blob/master/1/1.0.1/Dockerfile)

## License

Eclipse RDF4J is released under [Eclipse Distribution License 1.0 (BSD)](https://projects.eclipse.org/content/eclipse-distribution-license-1.0-bsd).

## How to start

You can start the docker containter for a quick test with
```
docker run -it --rm -p 8080:8080 yyz1989/rdf4j
```
