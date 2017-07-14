#  Persistent Identifiers and Open Citations: Basic Building Blocks of the Scholarly Web

20 Minutes

---

## Learning Objectives

* Recognize the essential role of Digital Object Identifiers (DOIs) for the scholarly web
* List reasons to use DOIs
* Identify components of a DOI
* Apply basic UNIX curl commands to test and resolve DOIs for research objects
* Explain how the DOI registration system is organized and what information it yields for authors.
* Practice basics of three command line tools useful for working with textual data from the World Wide Web:
    - `curl`
    - `jq`
    - `pandoc`

---

## Introduction

Digital Object Identifiers (DOIs) are unique names assigned to information resources (including research papers and datasets) that are represented in some way on the
Internet. DOIs represent an established international information standard, ISO26324:2012, and many publishers, data centers, and other information providers
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
specimen, or a scientific sample will specify the repository or collection
where that item resides.

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
published, who has published it, what works it cites, under what conditions the work was created and distributed (with what funding,
whether the work is available open access, whether the work has been updated
since publication, and more.)

In this session we'll explore the anatomy of a DOI, how it is generated, and how to retrieve the rich metadata associated with a given research object and its DOI.

Finally, we will add to our command line repetoire by practicing a few new tools to help us acquire, examine, and use scholarly metadata available on the Web.

- `curl`: a unix command for transferring data from or to an Internet server without human interaction. We will use `curl` to retrieve data from a DOI database and to negotiate for data in the format most convenient for our use.
- `jq`: a command-line tool that allows us to parse data in JSON (Javascript Object Notation) format. JSON is great for machines to understand but looks like gobbleygook to most humans. We will use `jq` to 'pretty print' data we retrieve from the DOI database
- `pandoc`: a 'swiss-army knife' tool for converting a document in one markup format to another format. We will use `pandoc` to convert html data we retrieve with `curl` to a `.docx` format for clean reading and printing. (_NOTE_: In other AuthorCarpentry lessons, `pandoc` is used to convert markdown (`.md`) files into nicely typeset `.pdf` format for electronic and print.)

---

### Exercise 1a. Practice using `curl` to interact with a World Wide Web site and retrieve a document from that site to a file on your desktop. Then display the file on your terminal.

    $ curl http://thinkchecksubmit.org/check/ -o think.html
    $ less think.html

What is the format of the retrieved content? Change the file extension to reflect the format of this web document

### Exercise 1b. Convert the file into a clean format for reading or printing using `pandoc`

    $ pandoc -o think.docx think.thml

Please note .docx instead of .doc, otherwise it doesn't work. Launch LibreOffice: how does the document look now? Will printing this document in this format look different than if you print it directly from the website?


TIP: _Feel free to send yourself a copy of this useful handout on how to assess whether a journal is reputable or not_

---

### Exercise 2a. Practice using `curl` to retrieve data from the DOI database, CrossRef,  and save to a file on your desktop. Then display the file on your terminal.

    $ curl -o shen.txt https://api.crossref.org/works/10.1186/s12916-015-0469-2
    $ less shen.txt

 What is the format of the retrieved content? Change the file extension to reflect the type of format this data is in.

### Exercise 2b. Use the jq tool to pretty print the file for easier human reading.

    $ jq . filename_from_previous_step > shen_pretty.json

Now that you can read the file more easily, you should be able to answer the following questions:

- what is the title of the document?
- how many references does this article cite?

---

### Exercise 3a. You just need the citation, not the entire metadata record for this research object. Use content negotation with the CrossRef database to just get the citation for this item, in APA style. View the result on your screen.

    $ curl -LH "Accept:text/x-bibliography; style=apa" https://doi.org/10.1186/s12916-015-0469-2

### Exercise 3b. It turns out that some other systems where you want to submit this citation data only take the open citation format, bibtex.  Perform content negotiation with the CrossRef database again, but this time require the citation in bibtex format. Save the output to a file on your desktop for later reuse.
(For example, the ORCiD researcher profile system and certain funding agencies' submission systems accespt bibtex citations).

    $ curl -LH "Accept:application/x-bibtex" https://doi.org/10.1186/s12916-015-0469-2 -o shen.bib

    $ less shen.bib

### Exercise 3c. Retrieve and save bibtex citations for three more research papers so you can complete your publication list for your project. Here are the DOIs for each paper:

- 10.1126/science.342.6154.60
- 10.3346/jkms.2017.32.5.713
- 10.1503/cmaj.109-4889


*Challenge question*: how could you use a single command line tool to quickly combine these citations into one file representing your publication list?

Solution
   
    $ cat file1.bib file2.bib file3.bib > publist.bib



---
### Exercise 4. The final step in your author carpentry DOI pipeline to make a 'publication list' with your works based on their DOIs. Can you apply the steps learned in Exercises 2+3 to accomplish this task?

HINT: You need to use content negotation with the DOI database to retrieve  citations for each DOI you have. Then combine the individual citations into a single file.  

Once you have a bibtex file with your DOIs and citations, you are ready to set up your ORCiD account and connect your author ID with your DOIs.`

---


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
data for a researcher. We'll look at this data throughout the rest of the
lesson.

<img src="img/Figure1.jpg" alt="Anatomy of a DOI" width="666" height ="371">

---

Next: [Register a DOI](01-register-doi.html)
