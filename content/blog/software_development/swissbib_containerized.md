---
title: "containerized environment for swissbib discovery"
author: "Günter Hipler"
description: "containers for libraries"
date: 2020-08-20T8:50:09+02:00
draft: true 

tags: [container]
categories: [software_development]

---


Every year, the apprentices of the University Library of Basel get the opportunity to get to know the tasks and projects of the IT department. A series of smaller workshops on selected topics is organised as part of these familiarisation weeks.  

One of these workshops introduced the topic of [container technologies](https://swissbib.gitlab.io/presentations/apprentices-docker-container).    

The author of the workshop took the topic as an opportunity to implement the swissbib discovery service with its various components (web application, search engine, database) as services in containers. As a result now everone is [able to download the container definition scripts](https://gitlab.com/swissbib/classic/docker_vufind)  and run a first functional library discovery service by themselve on own devices. To make first steps very easy: with the bootstraping of the containers nearly 20.000 documents are indexed to play around with a complete local discovery.   

Not only the web application is available. It is also possible to access the full-fledged distributed search engine [Solr](https://lucene.apache.org/solr/) which gives you the opportunity to get to know very closely search engine technology.  

Because container technolgy (especially Docker) is ubiquitous these days in general you are able to run the containers on different operating systems  
Linux     
Mac or   
Windows  

Linux is the easiest way to use Containertechnolgy. For [Mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac) and [Windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows) Docker provides easy to use so called "Docker Desktop environments".  
As disclosure: The author tried to install both environments on Mac and Windows. Indeed Mac was quite easy and after installation and restart of the system a complete docker and docker-compose environment was available ready to use the prepared scripts. The author wasn't able to install docker desktop on windows. Although he could use a Windows 10 Professional system (generously provided by the IT support of the library) he got the error message "cannot enable the Hper-V service". Because of time constraints the description in this post is limited to Linux and Mac. Would be great if someone could send a feedback if he/she is able to install the environment on Windows.
[Here](https://docs.docker.com/engine/install/ubuntu/) you can find the documentation to install Docker on Ubuntu Linux. Beside docker core you have to install [docker-compose](https://docs.docker.com/compose/install/) 

Now in short the few steps to follow the introduction by your own on your own device

* Install the Docker environment (sources above)  
* if Git version control system is installed on your system
  * git clone https://gitlab.com/swissbib/classic/docker_vufind.git
  * cd docker_vufind
  * git checkout workshop-apprentices
* if Git is not installed
  * https://gitlab.com/swissbib/classic/docker_vufind/-/tags/workshop-apprentices-v2
  * download one of the zipped files
  * extract the zipped file  
  
* run the wrapper script to start the complete environment    
<br/>

```bash

#this is just a simple wrapper script to start the docker bootstrapping, install the necessary Solr index schema and index the first documents 
./run.sh

#to stop the environment later you can use the prepared wrapper script ./stop.sh

```    

Once the script has finished (for the first time because the several images have to pulled it takes around 3 minutes) 8 containers are running and you are able to access the discoveryservice on localhost   

```bash

swissbib@ubuntu:~/temp/trash/test/docker_vufind-workshop-apprentices-v2$ docker-compose ps
           Name                         Command               State                          Ports                        
--------------------------------------------------------------------------------------------------------------------------
swissbib_vufind_apache_con   docker-php-entrypoint apac ...   Up      0.0.0.0:10000->80/tcp                               
swissbib_vufind_mysql_con    docker-entrypoint.sh mysqld      Up      3306/tcp, 33060/tcp                                 
swissbib_vufind_solr1_con    docker-entrypoint.sh solr- ...   Up      0.0.0.0:8981->8983/tcp                              
swissbib_vufind_solr2_con    docker-entrypoint.sh solr- ...   Up      0.0.0.0:8982->8983/tcp                              
swissbib_vufind_solr3_con    docker-entrypoint.sh solr- ...   Up      0.0.0.0:8983->8983/tcp                              
zoo1                         /docker-entrypoint.sh zkSe ...   Up      0.0.0.0:2181->2181/tcp, 2888/tcp, 3888/tcp, 8080/tcp
zoo2                         /docker-entrypoint.sh zkSe ...   Up      0.0.0.0:2182->2181/tcp, 2888/tcp, 3888/tcp, 8080/tcp
zoo3                         /docker-entrypoint.sh zkSe ...   Up      0.0.0.0:2183->2181/tcp, 2888/tcp, 3888/tcp, 8080/tcp


http://localhost:10000/Search/Results?lookfor=hello&type=AllFields&limit=20
```    


<img style=" width: 600px; height: 330px;" src="/image/sd/container_search_list.png"/>  

<br/> <br/>

additionally you have access to the backend of the distributed search engine Solr

```bash
http://localhost:8981/solr
```

<img style=" width: 480px; height: 330px;" src="/image/sd/solr_search.png"/>  
<img style=" width: 480px; height: 330px;" src="/image/sd/solr_cluster.png"/>  

    
It would be nice if you could give us feedback on the possibilities to use your own discovery service in an easy way.  

As already said: Today you can find container technology everywhere. It's the most important  pillar for the orchestration technolgy [Kubernetes](https://kubernetes.io/) which in turn forms the basis for the cloud platforms of almost all major providers. So running a discovery service in containers you can choose between Google, Amazon or your local university IT center for straight forward deplyoment mechanisms. The pain of the past, where you have to administrate with relativly high costs your server landscape by yourself is over. And of course you have no vendor specific lock-in.    
In the [memobase project](https://twitter.com/memoriav_ch/status/1227133102507601920) we are using the Kubernetes technology provided by the IT services of the University of Basle and of course most of the implemented microservices are containerized.       

<a href="https://swissbib.blogspot.com/2019/01/die-personen-hinter-swissbib-les.html" target="_blank">Author: Günter Hipler</a>

