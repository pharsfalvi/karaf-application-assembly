# karaf-application-assembly
Karaf customization assembly demo, building together an offline karaf application with pre-installed Camel, Drools and ActiveMQ features.

### Background

Apache Karaf has great feature for installing applications using the maven protocol. Applications can be defined as karaf features -  which are basically the superset of jar files and other features - which can be deployed easily from a maven repository. This is great for development, but not really good for production where usually the preferred way is to release the jar files together with the container.

This demo project puts together a customized karaf build with some pre-defined features, producing a container, which will run the predefined application components once you start it.

### Features

  * Branded console
  * Prebuilt offline repository, installed as part of the container
  * Preconfigured to run felix OSGi container
  * Customized instance name
  * Based on karaf 3.0.2
  * Windows and Unix support
  
  
### How to build and run

Check out the project and build it with maven
```
$ mvn clean install
```

Go to the target folder of assemble module
```
$ cd assemble/target/karaf-distro-demo-1.0.0-SNAPSHOT/karaf-distro-demo-1.0.0-SNAPSHOT/
```
Run karaf
```
$ bin/karaf
```

Once the container starts, it deploys all bundles (about 150) from its offline repository (about 50MB).
You can see that ActiveMQ, Camel, Drools features are installed

```
karaf@demo>feature:list -i
Name            | Version          | Installed | Repository                       | Description                                       
--------------------------------------------------------------------------------------------------------------------------------------
standard        | 3.0.2            | x         | standard-3.0.2                   | Karaf standard feature                            
config          | 3.0.2            | x         | standard-3.0.2                   | Provide OSGi ConfigAdmin support                  
region          | 3.0.2            | x         | standard-3.0.2                   | Provide Region Support                            
package         | 3.0.2            | x         | standard-3.0.2                   | Package commands and mbeans                       
http            | 3.0.2            | x         | standard-3.0.2                   | Implementation of the OSGI HTTP Service           
kar             | 3.0.2            | x         | standard-3.0.2                   | Provide KAR (KARaf archive) support               
ssh             | 3.0.2            | x         | standard-3.0.2                   | Provide a SSHd server on Karaf                    
management      | 3.0.2            | x         | standard-3.0.2                   | Provide a JMX MBeanServer and a set of MBeans in K
pax-jetty       | 8.1.15.v20140411 | x         | org.ops4j.pax.web-3.1.2          | Provide Jetty engine support                      
pax-http        | 3.1.2            | x         | org.ops4j.pax.web-3.1.2          | Implementation of the OSGI HTTP Service           
demo            | 1.0.0-SNAPSHOT   | x         |                                  |                                                   
xml-specs-api   | 1.9.0            | x         | camel-2.10.3                     |                                                   
camel           | 2.10.3           | x         | camel-2.10.3                     |                                                   
camel-core      | 2.10.3           | x         | camel-2.10.3                     |                                                   
camel-spring    | 2.10.3           | x         | camel-2.10.3                     |                                                   
camel-blueprint | 2.10.3           | x         | camel-2.10.3                     |                                                   
drools-common   | 6.1.0.Final      | x         | camel-drools-example-6.1.0.Final | Drools Commons                                    
drools-module   | 6.1.0.Final      | x         | camel-drools-example-6.1.0.Final | Drools core                                       
kie             | 6.1.0.Final      | x         | camel-drools-example-6.1.0.Final |                                                   
spring-dm       | 1.2.1            | x         | spring-3.0.2                     | Spring DM support                                 
spring          | 3.2.11.RELEASE_1 | x         | spring-3.0.2                     | Spring 3.2.x support                              
spring-tx       | 3.2.11.RELEASE_1 | x         | spring-3.0.2                     | Spring 3.2.x Transaction (TX) support             
cxf-specs       | 2.6.6            | x         | cxf-2.6.6                        |                                                   
activemq-client | 5.10.0           | x         | activemq-core-5.10.0             | ActiveMQ client libraries                         
activemq        | 5.10.0           | x         | activemq-core-5.10.0             | ActiveMQ broker libraries                         
```
