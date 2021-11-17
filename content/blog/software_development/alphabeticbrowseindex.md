---
title: "Modern, fast and flexible alphabetic browse index based on search engine technology"
author: "Günter Hipler"
description: "alphabetic browse index for libraries"
date: 2021-10-01T8:50:09+02:00
draft: false 
tags: [swisscollections]
categories: [software_development]
---

# The past 

Alphabetic browse indices were very popular in OPACs based on integrated library systems like Aleph 500.
They were mainly used by expert users or library staff and were an outstanding feature in specialists catalogs like the one for "Handschriften, Archive und Nachlässe" (manuscripts, archives and estates) - the predecessor of <a href="https://www.swisscollections.ch" target="_blank" >swisscollections</a>.

Over the years, the swissbib team has been repeatedly confronted with requests for an alphabetical browse index in the <a href="https://swissbib.ch/home_en.html" target="_blank" >swissbib discovery system</a>. Mainly because of time restrictions of a small development team and regular controversial discussions in the library community about the sense and purpose of an alphabetical index the decision for concrete development steps were regularly postponed.
Even commercial providers of by then new search engine based discovery systems didn't provide a solution for this request of their customers. We think: the main reason for this restrain was that alphabetic browse functionality in the OPAC era was based on a relational database solution as the core component of an integrated library system.
It wasn't so easy to implement the same functionality based on search engine technology. 

What are the reasons for this difficulty. From my point of view because Browsing is not the same as Searching. With browsing people know exactly at which point of an index ("old" card catalogs) they can start their alphabetical browsing and then follow entry by entry manually.
With searching you have all kinds of sophisticated look ups on most of the time analyzed terms part of an index which is done by a search engine. While it might be possible to simulate an "entry" into a terms posting list (for example all the A-Z lists functionalities might be based on this) you will get definitely difficulties to simulate the alphabetic browsing of a user trying to look up entry after entry in such a posting list with analyzed terms of an optimized search index in an alphabetic order - no lookups as it is done by search requests. This was frankly not the purpose of the search index design.   

I think this is the reason why the rare implementations of the browse functionality nowadays (if there are any at all) use in some way a relational database in the background to simulate the step by step behaviour of users.

Often, when commercial product providers (like the one of Primo) have difficulties to implement a desire of users they start to argue in an arrogant manner like:
- browsing is only something for old and backward oriented librarians
- but look for google they also do not offer this functionality. And we all just want to be "googlers"

Not only because of our contractual obligations with the swisscollections association to implement browsing functionality like the one in Aleph, but also because such arguments from commercial vendors spur us on to provide good and better solutions with open software which fit the needs of our users.

We (our team) have to confess that we haven't had a lot of experience with browse indices in integrated library systems (maybe because we heard so often the arguments of commercial providers or because we are simply no longer accustomed to the systems that were mostly used until nearly 10 years ago ) But once the first version of the functionality was implemented in <a  target="_blank" href="https://swisscollections.ch/Alphabrowse/Home">swisscollections </a> and especially after we had realized the enrichment possibilities with alternative terms from the  <a href="https://www.dnb.de/EN/Professionell/Standardisierung/GND/gnd_node.html" target="_blank">GND</a> than part of the lists (not published for the productive frontend by 17.11.2021), we realized how interesting a "finding aid" like that of alphabetical browsing can be with a variety of different entry points in the form of scrollable indices.

Now, where most of the traditional Webopacs are migrated to commercial discovery solutions like <a  target="_blank" href="https://exlibrisgroup.com/products/primo-discovery-service/">Primo</a> it isn't so easy to find a still public accessible alphabetic browse feature.

Below a screenshot of such a solution from:  <a  target="_blank" href="https://aleph.mpg.de/F/?func=file&file_name=find-b&local_base=mpg01">Max Planck Society, Germany </a> 


<a href="/image/sd/swisscollections/alphabetic_browse_aleph_mpg.png" target="_blank"><img style=" width: 80%; height: 80%;" src="/image/sd/swisscollections/alphabetic_browse_aleph_mpg.png"/></a>

------------------------

figure 1, example of an alphabetic browse index based on the Aleph 500 System
-----------------------

<br/>
<br/>

# available current solutions

Our team is currently aware of two implementations for alphabetical list browsing within a search engine based discovery solution
One is the Open Source solution of VuFind <a href="https://vufind.org/demo/Alphabrowse/Home" target="_blank">in a demo version </a> and as part of <a href="https://library.villanova.edu/Find/Alphabrowse/Home" target="_blank">a productive environment</a>.
The other one is the commercial <a href="https://slsp-ubs.primo.exlibrisgroup.com/discovery/browse?vid=41SLSP_UBS:live" target="_blank">Primo</a> product

Because we are using VuFind as the basis for the swisscollections frontend just at the beginning of the project it was our firm idea to use the VuFind implementation for our requiremnt.

## (short) description and evaluation of the VuFind mechanism in the context of our requirements 
Because of the open source character it is easy to analyze how the functionality is implemented. The main documentation is this

- <a href="https://vufind.org/wiki/indexing:alphabetical_heading_browse" target="_blank"> vufind doc </a> 
- <a href="https://teaspoon-consulting.com/articles/vufind-browse-handler.html" target="_blank">an article by Mark Triggs</a> 
- <a href="https://github.com/vufind-org/vufind-browse-handler" target="_blank"> implementation of a solr plugin and customized analyzers as part of the solution</a> 

We gave ourselves more than a week to understand the implementation and to consider whether and how we can integrate it into our overall system and whether it meets the requirements of the swisscollections association. As a summary our findings and conclusions:

- "VuFind Alphabetical Heading Browse" ("VAHB") is mainly designed for a Solr Index with a single shard
- Often Solr is used as single node server and the deployment is mostly side by side with the VuFind web-application
- There are some shell scripts which can be used for terms extraction of an existing Solr core. These terms are then analyzed (via provided custom analyzers) and stored within a relational file based database (SQLite)
- the database with the (sorted) terms of the index is then deployed side-by-side with the Solr server which makes it possible for a deployed Solr-plugin to access the sorted terms in the database.
- VAHB solutions known to us offer only a small number of indices (e.g. four in the <a href="https://library.villanova.edu/Find/Alphabrowse/Home" target="_blank"> Villanovy discovery</a>)
- the implentation is a little bit outdated. E.g. ant is used as a build tool and we haven't seen the possibility to use managed dependencies.

As part of the evaluation we implemented two prototypes to get a deeper understanding if and how it could match our requirements
- first a <a href="https://gitlab.com/guenterh/vufind_alphabetic_browse_prototype/-/tree/main" target="blank">gradle multi project</a> to overcome the unmanged dependencies. This was possible with the exception of the MarcImporter.jar where we couldn't find a suitable component so we had to define a <a href="https://gitlab.com/guenterh/vufind_alphabetic_browse_prototype/-/blob/main/common/build.gradle#L24">file based lib </a>
- because it would be very unnatural (if not impossible) to use the script based workflows within our Kafka based microservice environment we implemented a quick prototype <a href="https://gitlab.com/guenterh/browse-index-creator/-/blob/master/src/main/scala/ch/swisscollections/Main.scala">as a consumer for Kafka</a> to insert new/updated values into a relational sql database (in our case MariaDB to access it via network as a shared database)

Perhaps such prototypes might be helpful for the further development of the original VuFind artefacts. Later in the year 2021 (when we had already completed our solution) we saw that others are also working on the integration into <a href="https://sourceforge.net/p/vufind/mailman/vufind-tech/thread/BL1PR03MB61362FE7F954C69114F985CDE8F79%40BL1PR03MB6136.namprd03.prod.outlook.com/#msg37333469" target="_blank">multi node SolrCloud environments</a>

On the other side the solution should be able to fit well into our environment and the requirements . Here are some key points:
- workflows should be able to be fully automated. Whenever possible, a service should be based on event-based mechanisms and obtain its information from a log-based system (in our case Apache Kafka)
- we are using a SolrCloud cluster with multiple nodes and collections with multiple shards and replicas.
- we are trying to avoid any manually work. The cluster is set up on remote servers, collections are created via the Solr API, Solr configurations are stored in Zookeeper-Ensembles, we use productive fallback and seperated test clusters. All this would make it difficult to use file-based databases and customized SolrHandler-jars being part of the classpath of the Solr-Clusters
- at the moment the swisscollections association wants to provide 79 different indices. We doubt that such a requirement is compatible with a database supported solution.
- every day there are a lot of inserts / updates and deletes of the whole swisscollections repository. Not so much as in the times of <a href="https://www.swissbib.ch" target="_blank">the swissbib solution</a> where we got between 100.000 and 500.000 events / day but there is quite a lot. In the past these updates were processed once a day, now we have in mind to process them every 2 hours. Would it be possible to update the sorted terms in the database so often? We doubt this.
If you are interested in more details of our discussion you can find <a href="http://www.iwerk.ch/swisscollections/discussion_use_of_current_vufind_mechanism.pdf" target="_blank">here a pdf</a> with some additional notes. (by now only in German - if there is more interest we could translate it in English - let us know).


# Which solution have we chosen?
From the evaluation of "VAHB", we realised that we should do without a database-supported solution as far as possible. This was in line with our original wish to implement a complete search engine-based functionality as far as possible. But how to do this. Some of the possibilities we discussed:
- something like autosuggestion as it is done in our old swissbib service
- using the <a href="https://solr.apache.org/guide/8_8/field-types-included-with-solr.html" target="_blank">SortableTextField"</a> type of Solr?
- using the range query functionality of Solr?
- use of the <a href="https://solr.apache.org/guide/8_10/the-terms-component.html" target="_blank" >Solr terms component</a>

Again, if you are interested in more details of our discussion you can find <a href="http://www.iwerk.ch/swisscollections/alternatives_discussion_alternatives_search_engine_based_solutions.pdf" target="_blank">here</a> a recording of our arguments

- The Solr terms seemed very fast a natural fit for requirements for alphabetic browsing. You can easily pick up a start point in the list of the terms and after this start point you can get the next terms step by step in the (alphabetic) sort order of the index.
- The terms to be indexed can be analyzed with the desired analyzers

But then the difficulties pop up. Two of the most serious:
- Although you want to browse through the analyzed terms users are only interested in the original values. Is it possible to create any relation between the analyzed terms in the Solr terms list and the values to be shown to the user? In the database of the "VAHB" solution this relation is done via two separate columns in Sqlite database
- the Solr terms component doesn't provide any analyzing functionality for the values the users send to the search engine. The aim of the terms component is a very fast lookup for terms in a list.

It quickly became clear that we could not adopt this initially obvious option one-to-one.


# components and details of the implemented solution

In general a solution should consist of three parts:
- a) in the middle the Solr terms component for a quick entry point to the list and the possibility of using the next following terms in alphabetical order
- b) a service for preparing all the terms of all the 79 indices. Additionally, these terms should contain a reference to the value to be displayed and relations to variants and IDs coming from authority repositories like the GND.
- c) a service (API) for analyzing the user values in the same way as it is done with b)
- d) the response of the API (for the swisscollections frontend client) should be a simple JSon format of all these parts plus the number of documents for the value in the list (which is already a functionality of the terms component)

<a href="https://gitlab.com/swissbib/swisscollections/browse-index-values" target="_blank">browse-index-values</a>   --->> swisscollections Solr cluster <<---   <a href="https://gitlab.com/swissbib/swisscollections/termsquery-analysis-api" target="_blank">termsquery-analysis-api</a>   <<--- <a href="https://swisscollections.ch/Alphabrowse/Home" target="_blank">the swisscollections frontend</a>

todo: create a picture for this - probably in confluence

## some details of the solution

### browse-index-values
@Silvia ??

### termsquery-analysis-api
@Silvia?

### other stuff?? 


# problems of the solution and how we solved it
todo: Günter / Silvia

# some (short) notes related to Apache Kafka and why we use it
During the last VuFind summit 2021 our colleagues Lionel Walter and Christoph Böhm (links fehlen noch)
https://vufind.org/docs/summit2021/walter-bohm.pdf
https://www.youtube.com/playlist?list=PL5_8_wT3JpgEw-ceaAxXChm7jTpV8cV3X recording fehlt noch

introduced some of the swisscollections functionalities in a presentation. They have spoken (shortly) about the Apache Kafka platform we use as the central backbone for all our backend services. At this point, I would like to briefly take the opportunity to introduce a few principles of this platform and briefly explain why they are so valuable for us.
more to come




