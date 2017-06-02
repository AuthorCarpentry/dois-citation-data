#  Persistent Identifiers and Open Citations: Basic Building Blocks of the Scholarly Web 

20 Minutes

---

## Learning Objectives

* Recognize the essential role of Digital Object Identifiers for the scholarly web
* List reasons to use DOIs 
* Identify components of a DOI
* Apply basic curl commands to test and resolve DOIs for research objects
* Explain how the DOI registration system is organized and what information it yields for authors

---

## Introduction

Digital Object Identifiers (DOIs) are unique names assigned to research outputs
and other information resources that are represented in some way on the
Internet. DOIs represent an established international information standard, ISO
26324:2012, and many publishers, data centers, and other information providers
rely on this standard to assign unique identifiers for works under their care.
The DOI assigned to a given research object distinguishes it from other works,
including other versions of the same intellectual material. Examples of
research-related information resources assigned DOIs include journal articles,
curated datasets, theses, conference papers, pre-prints, technical reports, and
books.

DOIs are actionable on the Internet: when put in URL form
(https://doi.org/{DOI}, these strings automatically redirect to an online
landing page that offers information about the research object.  Often, but not
always, the landing page contains a link to the resource itself. Where the
resource is not online, the landing page indicates where to find it. For
example, a DOI assigned to a physical resource such as a print book, a museum
specimen, or a of scientific sample will specify the repository or collection
where the resource resides.

The DOI is NOT by itself a seal of quality. Yet information resources that are
assigned DOIs tend to be of enduring value; are likely to be used and cited by
others; and are maintained by a publisher or other information provider who is
committed to curating and preserving the resource over time. Because an
organization is committed to curating the resource over time, the DOI is
considered persistent. Some say that the DOI is basically a promise to always
supply information about the information resource associated with the
identifier.

A DOI is considered a persistent identifier because it reliably resolves to a
human- and machine-readable landing page representing the information resource.
But the DOI itself is not a guarantee that the dataset or paper is available
via Open Access: rather, the DOI resolves to an Open Access landing page that
may (or may not) permit linking through to the desired object. Whether or not a
user can access the full content depends on various circumstances unrelated to
the DOI system: format of the resource, restrictions and conditions governing
access; authentication requirements; software compatibility; etc.

Nonetheless, the metadata associated with the DOI is rich enough to provide
useful data for researchers. DOI metadata can tell alot about what has been
published, who has published it, under what conditions (with what funding,
whether the work is available open access, whether the work has been updated
since publication, and more.)

This lesson explores the anatomy of a DOI, how it is generated, what metadata
is associated, and how to get a DOI for a new work.

---

> ## Exercise 1A. Demonstrate that a DOI redirects to a landing page for an
> ## associated information resource.
>
> > ## Solution 1A
> >
> > `$ curl -s -S http://dx.doi.org/10.1103/PhysRev.109.193`
> > 
> > `$ curl -s -S http://dx.doi.org/10.7935/K5H41PBP`
> > 
> > *Whose websites did the redirects for each DOI take you to?*

---

> ## Exercise 1B. Resolve a DOI to a landing page to confirm its validity,
> ## and determine the title of the associated digital object.
>
> > ## Solution 1B
> >
> > `$ curl  -s -S -L http://dx.doi.org/10.1103/PhysRevLett.116.061102 >redirect1.txt`
> > 
> > `$ grep "citation_title" redirect1.txt`
> > 
> > `$ curl -s -S -L http://dx.doi.org/10.7935/K5H41PBP >redirect2.txt`
> > 
> > `$ grep "title" redirect2.txt`

---

> ## Exercise 1C. Determine if a 'DOI-style string' is a valid DOI.
> 
> > ## Solution 1C
> > 
> > `$ curl -s -S -L http://dx.doi.org/10.5454/JPSv1i220161014 | grep "title"`
> > 
> > Note: The faux DOI used in this example was assigned by an established
> > publisher to detect and block unauthorized access to their system. The
> > controversy surrounding publisher creation of DOI-like strings for business
> > operations was taken up in an interesting posting on the CrossRef blog, [DOI
> > like strings and fake DOIs]
> > (http://blog.crossref.org/2016/06/doi-like-strings-and-fake-dois.html).

---

> ## Exercise 1D. Retrieve the landing page for a DOI object and "pretty
> ## print" the output to something easier on the eyes.
> 
> > ## Solution 1D
> > 
> > `$ curl -s -S -L http://dx.doi.org/10.7935/K5MW2F23 >ex1A4.txt`
> > 
> > `$ less ex1A4.txt`
> >
> > What format is the landing page provided in?
> > 
> > To make the retrieved data easier to read, remove the markup using the the Unix
> > stream editor sed. A regular expression is used to represent all unwanted
> > content between html brackets.
> > 
> > `$ sed -e 's/<[^>]*>//g' ex1A4.txt > ex1A4_pretty.txt`

## Anatomy of a DOI

The [International DOI System](https://www.doi.org/) is the overall
infrastructure by which Digital Object Identifiers are assigned, registered,
resolved, and associated with valuable metadata including citation,
availability of full text, funder information, licensing information, and more.
The following components of the DOI System together make it work:

+ The [International DOI Federation (IDF)](http://www.doi.org/doi_handbook/7_IDF.html) 
is responsible for the overall governance of the system. IDF is a not-for-profit membership
organization that oversees the operations of the federation of Registration
Agencies which provide Digital Object Identifier (DOI) services and
registration. IDF is also the registration authority for the ISO standard (ISO
26324) for the DOI system.

+ [Registration Agencies (RAs)](https://www.doi.org/registration_agencies.html)
provide services to Registrants (or Members) — allocating DOI name prefixes,
registering DOI names and providing the necessary infrastructure to allow
Registrants to declare and maintain metadata and state data. Each RA must
follow basic protocols and standards of the DOI sytem, including a minimum
metadata standard known as the DOI kernel. Yet each RA has the freedom to
implement additional metadata standards, track a range of information about a
given DOI resource, and offer public services for querying their databases. As
an example, the Registration Agency CrossRef registers a range of metadata
about scholarly resources including funding data, license associated with the
digital object, author data including ORCiD numbers, and more -- see April
Ondis' CrossRef Blog posting 
[Beyond the DOI to richer metadata](http://blog.crossref.org/2016/06/beyond-the-doi-to-richer-metadata.html)
for more info about their services.

+ Registrants (or Members) of a given Registration Agency register DOIs for
information resources under their responsibility. Registrants include
publishers, data centers, universities, libraries, university presses, and open
data sharing repositories such as Zenodo. Registrants must follow the policies
and procedures established by the RA in order to register DOIs. Each Registrant
is given a unique member code that uniquely distinguishes them amongst all
members of the RA. Each member also receives one or more unique prefix codes
that forms the first part of the DOI sequence. The Registrant then uses the
suffix portion of the DOI sequence to assign unique names to each resource they
manage.

The metadata associated with the DOI is often rich enough to provide useful
data for a researcher. This lesson and the next look at the array of useful
public data associated with DOIs.

![Anatomy of a DOI](img/Figure1.jpg")

---

> ## Exercise 1E. Demonstrate that a DOI redirects to the landing page for an
> ## associated digital object and retrieve the content of the landing page.
> 
> > ## Solution 1E
> > 
> > `$ curl -s -S -L http://dx.doi.org/10.1103/PhysRev.109.193 >landing1.txt`
> > 
> > `$ curl -s -S -L http://dx.doi.org/10.7935/K5H41PBP >landing2.txt`
> > 
> > `$ wc landing*.txt`

---

> ## Exercise 1F. Given a DOI, determine which Registration Agency issued it.
> 
> > ## Solution 1F
> > 
> > `$ curl http://doi.crossref.org/doiRA/10.5170/CERN-2000-001.101`
> > 
> > `$ curl http://doi.crossref.org/doiRA/10.5170/CERN-2000-001.101,
> > doi.crossref.org/doiRA/10.2307/1578389`
> > Note that this handy lookup service is provided by one of the Registration
> > Agencies, CrossRef, yet the query also works for DOIs issued by other
> > Registration Agencies! This demonstrates that each DOI Agency provides an
> > array
> > of services beyond registering and maintaining DOIs for their members;
> > savvy
> > researchers may wish to check with more than one RA to get useful
> > information.

---

> ## Exercise 1G. Retrieve a list of DataCite members and determine the format of the data provided
>
> > ## Solution 1G
> >
> > `$ curl -s -S http://api.datacite.org/members >datacite.txt`
> > 
> > `$ less datacite.txt`
> > Note that the data comes from the Datacite API in JSON format (Javascript
> > Object Notation) -- an increasingly popular metadata standard for Web
> > services.
> > JSON is great for machines to read, but not so much for humans! So let's
> > convert it to something easier on the eyes.
> > 
> > `$ cat datacite.txt | tr ',' '\012' >datacite_pretty.txt`
> > `$ less datacite_pretty.txt`

---

Next: [Register a DOI](01-register-doi.html)
