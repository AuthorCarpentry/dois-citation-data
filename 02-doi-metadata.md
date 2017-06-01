# DOI Metadata

15 min

------

Learning Objectives:

* Retrieve the metadata associated with a DOI
* Apply content negotiation commands to obtain a citation for a given DOI in a
preferred style (e.g. BibTeX  or APA) from the CrossRef API 
* Gain experience with Bash command line tools to concatenate the citations
into a single BibTeX publication list for reuse

------

When works are registered with DOI Registration Agencies, the Registrant
(publisher, data center, or other information provider) is required to submit
metadata about the resource that the DOI links to. Each Registration Agency
maintains its own metadata schema and establishes rules for requiring and
populating the metadata elements so it is important to check their respective
websites for a list of metadata elements used and whether they are mandatory or
optional.

Each Registration Agency also has the option of offering metadata look up and
harvesting services that researchers may openly query. At a minimum, these
services provide a basic citation for each DOI-assigned work: creator, title,
publisher, publication year, and URL for the landing page of the resource.
Additional metadata may include references cited in the work; funding sources;
author ORCiD numbers; usage licenses attached to the work; and more.

Researchers may search for metadata associated with DOIs in various ways. This
module demonstrates how to use the API services of two Registration Agencies --
CrossRef and DataCite -- to query and retrieve valuable metadata about research
outputs. The commands demonstrated use the process of DOI Content Negotiation
to retrieve different representations of a work from the API service.

---

> ## Exercise 1C(1). Query the Registration Agency API to retrieve a citation
> ## for a published article.
> 
> > ## Solution 1C(1)
> > `$ curl http://api.crossref.org/works/http://dx.doi.org/10.1103/PhysRevLett.116.061102 > cite1.txt`
> > 
> > `$ less cite1.txt`
> > 
> > The retrieved citation is in JSON format -- a popular way for presenting
> > citation metadata that can be parsed by machines. But what if you need a
> > different citation format for your purposes? Let's try Content Negotation to
> > specify that we want the citation provided in BibTeX, a citation format used in
> > many research information systems.
> > 
> > `$ curl -LH "Accept:text/bibliography; style=bibtex" http://dx.doi.org/10.1103/PhysRevLett.116.061102 > cite1.bib | cat cite1.bib |tr ',' '\012'`
> > 
> > Do you know of any research information services that automatically ingest
> > citations in BibTeX? **(Cue the ORCiD system) Keep this citation in its BibTeX
> > for Lessons 2 and 3, where we add it to a publications list to cite in a new
> > research paper.**

---

> ## Grande Finale! Exercise 1D(2). Retrieve a list of work types that arevassigned DOI's by DataCite.
> 
> > ## Solution 1D(2)
> > This exercise applies various UNIX commands to answer the question "What types
> > of works can be assigned DataCite DOI's and how many types?"
> > 
> > `$ curl https://api.datacite.org/work-types > works_raw.txt`
> > `$ head works_raw.txt`
> > `$ cat works_raw.txt | tr ',' '\012' > works_clean.txt`
> > `$ cat works_clean.txt | grep "title" | cut -d : -f 3 > works_final.txt`
> > `$ cat works_final.txt | wc -l`

---

---

> ## Exercise 2B. Creating a file of BibTeX citations
> Fetch several references from an open database on the Web and
> use them to compose a bibliography.
>
> > ## Solution 2B
> > Save each citation in BibTeX format for reuse (e.g., save as cite1.bib,
> > cite2.bib, etc.). Concatenate the individual BibTeX citations into one
> > bibliography
> > using command line tools:
> >
> > `$cat cite1.bib, cite2.bib, cite3 bib > citations.bib`
> > 
> > `$cat citations.bib`
> > 
> > Everything look okay? Save that concatenated file

---

Previous: [Register a DOI](01-register-doi.html)
