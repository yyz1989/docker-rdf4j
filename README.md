# Eclipse RDF4J

## Introduction

This is the Docker repository for RDF4J Server (which is RDF database server and the SPARQL endpoint service) and RDF4J Workbench (which is the Web UI of RDF4J Server for database and data management tasks). Eclipse RDF4J is the official successor to the OpenRDF Sesame framework. For more information about RDF4J, please refer to [Eclipse RDF4J Official Website](http://rdf4j.org/).

RDF4J is currently released with two version series 2.x and 1.x, where 2.x is the successor of Sesame 4.1 requiring Java 8 Runtime Environment and 1.x is the corresponding Java 7 backport. Accordingly, this Docker repository also includes both versions, with supported tags and Dockerfiles listed as follows:
* `2.4.4`, `2.4`, `2`, `latest`: Built with JRE 8 and Tomcat 8.5 [Dockerfile](https://github.com/yyz1989/docker-rdf4j/blob/master/2/2.4/2.4.4/Dockerfile)
* `2.3.3`, `2.3`: Built with JRE 8 and Tomcat 8.5 [Dockerfile](https://github.com/yyz1989/docker-rdf4j/blob/master/2/2.3.3/Dockerfile)
* `2.2.4`, `2.2`: Built with JRE 8 and Tomcat 8.5 [Dockerfile](https://github.com/yyz1989/docker-rdf4j/blob/master/2/2.2.4/Dockerfile)
* `2.1.6`, `2.1`: Built with JRE 8 and Tomcat 8.5 [Dockerfile](https://github.com/yyz1989/docker-rdf4j/blob/master/2/2.1.6/Dockerfile)
* `2.0.3`, `2.0`: Built with JRE 8 and Tomcat 8.5 [Dockerfile](https://github.com/yyz1989/docker-rdf4j/blob/master/2/2.0.3/Dockerfile)
* `1.0.3`, `1`: Built with JRE 7 and Tomcat 8 [Dockerfile](https://github.com/yyz1989/docker-rdf4j/blob/master/1/1.0.3/Dockerfile)

RDF4J Server and RDF4J Workbench also require a Java Servlet Container that supports Java Servlet API 2.5 and Java Server Pages (JSP) 2.0. In this Docker repository, Tomcat is used as Servlet container in all Docker images.

## License

Eclipse RDF4J is released under [Eclipse Distribution License 1.0 (BSD)](https://projects.eclipse.org/content/eclipse-distribution-license-1.0-bsd).

## How to start

A docker containter can be started for a quick test with
```
docker run --rm -p 8080:8080 yyz1989/rdf4j
```
In this case Tomcat will run in foreground and tail its log, where you can diagnose the status immediately.

## Port

By default only port 8080 for Tomcat is exposed.

## Volume

By default only the path `/opt/eclipse-rdf4j-${RDF4J_VERSION}/data` (where `${RDF4J_VERSION}` is the RDF4J release version in the Docker image) is exposed as mount point to the native host or other containers, since it is used by RDF4J Server to store configurations and persist database.

## Environment Variables

The following environment variables are used in the Docker images:
* `RDF4J_DATA`: the path of RDF4J Server working directory. The default value is `/opt/eclipse-rdf4j-${RDF4J_VERSION}/data`, which is exposed as mount point as aformentioned.
* `JVM_PARAMS`: additional JVM parameters passed to Tomcat. Please tune this value according to the use case. The default value is `-Xmx4g`.

Those two environment variables can be overriden with Docker parameter ```-e```, for example
```
docker run -d --rm -p 8080:8080 -e RDF4J_DATA=/data -e JVM_PARAMS="-Xms1g -Xmx8g" yyz1989/rdf4j
```
changes the JVM minimum and maximum heap size to 1 GB and 8 GB respectively, and RDF4J Server working directory to `/data`. A host directory can also be mounted into the container to persist data in production environment with
```
docker run -d --rm -p 8080:8080 -e RDF4J_DATA=/data -v /opt/rdf4j-data:/data -e JVM_PARAMS="-Xms1g -Xmx8g" yyz1989/rdf4j
```
