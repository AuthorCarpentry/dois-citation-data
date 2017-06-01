#  What are Digital Object Identifiers and Why Do They Matter to Researchers ?
10 Minutes

-------------------------

## Learning Objectives

* Understand Digital Object Identifiers and reasons to use them
* Use basic curl commands
* Resolve a valid Digital Object Identifier to an online landing page to determine what information is returned
* Test an invalid Digital Object Identifier (a DOI-like string) to determine what information is returned

-------------------------

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
(http://dx.doi.org/{DOI}, these strings automatically redirect to an online
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

### Exercise 1A(1). Demonstrate that a DOI redirects to a landing page for an
associated information resource.

`$ curl -s -S http://dx.doi.org/10.1103/PhysRev.109.193`

`$ curl -s -S http://dx.doi.org/10.7935/K5H41PBP`

*Whose websites did the redirects for each DOI take you to?*

### Exercise 1A(2). Resolve a DOI to a landing page to confirm its validity,
and determine the title of the associated digital object.

`$ curl  -s -S -L http://dx.doi.org/10.1103/PhysRevLett.116.061102
>redirect1.txt`

`$ grep "citation_title" redirect1.txt`

`$ curl -s -S -L http://dx.doi.org/10.7935/K5H41PBP >redirect2.txt`

`$ grep "title" redirect2.txt`

### Exercise 1A(3). Determine if a 'DOI-style string' is a valid DOI

`$ curl -s -S -L http://dx.doi.org/10.5454/JPSv1i220161014 | grep "title"`

Note: The faux DOI used in this example was assigned by an established
publisher to detect and block unauthorized access to their system. The
controversy surrounding publisher creation of DOI-like strings for business
operations was taken up in an interesting posting on the CrossRef blog, [DOI
like strings and fake DOIs]
(http://blog.crossref.org/2016/06/doi-like-strings-and-fake-dois.html).

### Exercise 1A(4). Retrieve the landing page for a DOI object and "pretty
print" the output to something easier on the eyes

`$ curl -s -S -L http://dx.doi.org/10.7935/K5MW2F23 >ex1A4.txt`
`$ less ex1A4.txt`

What format is the landing page provided in?

To make the retrieved data easier to read, remove the markup using the the Unix
stream editor sed. A regular expression is used to represent all unwanted
content between html brackets.

`$ sed -e 's/<[^>]*>//g' ex1A4.txt > ex1A4_pretty.txt`

---


Next: [Anatomy of the DOI System](01-anatomy-doi.html)