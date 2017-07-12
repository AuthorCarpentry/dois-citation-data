Author Carpentry : Persistent access for research outputs with Digital Object Identifiers
=======

*Content Contributors: Gail Clement, Tom Morrell*

*Lesson Maintainers: Gail Clement, Tom Morrell*

**Lesson status: Active**

  * Taught at [CODATA-RDA Research Data Science Summer School, July 10-17, 2017](http://indico.ictp.it/event/7974/) and the [Force11 Scholarly Communication Institute, August 1-4, 2017](https://www.force11.org/node/7786/#wt3)
  * Piloted at [CODATA-RDA Research Data Science Summer School, August 2-16, 2016](http://indico.ictp.it/event/7658/)

## What you will learn:

* Recognize the essential role of Digital Object Identifiers as building blocks on the scholarly web
* List reasons to use DOIs
* Identify components of a DOI
* Apply basic UNIX curl commands to test and resolve DOIs for research objects
* Explain how the DOI registration system is organized and what information it yields for authors
* Register a DOI for a scholarly work using an open repository
* Create appropriate metadata to describe a new work and mint a DOI for it
* Retrieve the metadata associated with a DOI
* Apply content negotiation commands to obtain a citation for a given DOI in a preferred style (e.g. BibTeX  or APA) from the CrossRef API
* Gain experience with command line tools to:
- parse DOI metadata in JSON (Javascript Object Notation) format;
- convert documents in one markup format to another format
- concatenate  citations into a single BibTeX publication list for reuse in other researcher systems (ORCiD; MySciEnCV; Latex)

## Topics:

1. [Intro](00-intro-dois.html)
2. [Register a DOI](01-register-doi.html)
3. [DOI Metadata](02-doi-metadata.html)

## Requirements

Author Carpentry's teaching is hands-on, so participants are encouraged to use
their own computers to insure the proper setup of tools for an efficient
workflow.

You should have a list of publications (with a few DOIs) and a scholarly object (like a presentation, data set, report, or photo) that you are willing to share in an
open repository with an associated DOI.

This lesson requires basic familiarity with the bash shell, simmilar to the
experience gained through the
[Software Carpentry shell lesson](http://swcarpentry.github.io/shell-novice/).
You'll need to have a bash shell installed, you can follow
[these instructions](https://swcarpentry.github.io/workshop-template/#setup).

Your computer will also need to have running the open source json parsing tool, jQuery, available at:
 [jq json parser](https://stedolan.github.io/jq/) to be able to 'pretty print' json data retrieved from API services
and pandoc, the universal document converter, available at:
[pandoc](https://pandoc.org/).

## Cheat Sheet
jQuery (jq) Quick API Reference, https://oscarotero.com/jquery/

## References

+ curl documentation, 2016. https://curl.haxx.se/
+ CrossRef REST API, 2016.
https://github.com/CrossRef/rest-api-doc/blob/master/rest_api.md
+ Beyond the DOI to richer metadata, CrossRef Blog posting of June 15, 2016 by
April Ondis,
http://blog.crossref.org/2016/06/beyond-the-doi-to-richer-metadata.html
+ DataCite API, https://api.datacite.org/
+ Digital Object Identifier (DOI) Handbook, https://www.doi.org/hb.html
+ Digital Object Identifier System and DOI Names (DOIs) Guide from Australian
National Data Service, http://www.ands.org.au/guides/doi
+ DOI Citation Formatter beta, http://crosscite.org/citeproc/
+ jq online testing tool, https://jqplay.org/
+ Parsing JSON with jq, http://www.compciv.org/recipes/cli/jq-for-parsing-json/
+ Pandoc User Manual, http://pandoc.org/MANUAL.html
