# Register a DOI

15 min

------

Learning Objectives:
* Use an open repository (Zenodo) to obtain a DOI for a scholarly work

------

## Open repositories

Open science and [FAIR principles]{https://www.force11.org/group/fairgroup/fairprinciples}
encourage scholars to put more of their content online in an open format.
Scholarly works can be added online repositories that centralize, store, and
share the results.  Most repositories will be associated with a DOI
Registration Agency and will generate DOIs for every item that is stored.
Generating a DOI is one factor that you can use to determine whether a
repository is trustworthy.  There are different types of repositories that may
be appropriate for your scholarly works.

### Domain-specific repositories

There are many repositories that focus on a specific type of data or data from
a certain field.  If one exists for your data, subject specific repositories
are great because individuals looking for a specific type of data will know to
check that repository.  A subject-specific repository can collect data from
researchers around the world and customize the way the data is displayed.  This
can make it easier to find and reuse the data.  One challenge for
domain-specific repositories is ensuring a consistent source of funding-you
should monitor the repositories you use to ensure that your data remains
available.  

You can find a good listing of subject-specific repositories at
[PloS]{http://journals.plos.org/plosone/s/data-availability#loc-recommended-repositories}.  
A more complete list of repositories is available at [re3data]{www.re3data.org}

### Institutional repositories

Many institutions host data repositories, often through the library, to preserve the data collected at the
institution.  These repositories are often general and can take any scholarly
works that are associated with the institution.  Because these repositories are
associated with an institution, they may have a more consistent source of
funding.  However, they often do not have the customization available in a
domain-specific repository.

An example of an institutional data repository is
[CaltechDATA](data.caltech.edu)

### General repositories

A number of general repositories exist that can collect any type of scholarly
output.  These can be associated with a publisher, like 
[Mendeley Data]{https://data.mendeley.com/} or
[Figshare]{https://figshare.com/}.  Some institutions also run general
repositories that are open to all, like the 
[Harvard Dataverse]{https://dataverse.harvard.edu/}, 
[Dryad]{http://datadryad.org/}, or
[Zenodo]{https://www.zenodo.org/}. These general repositories can be free 
(Mendeley Data, Harvard Dataverse, Zenodo), charge per submission (Dryad),
or have size limitations (Figshare). We're going to use Zenodo because it is
free, open, and associated with CERN which provides institutional backing and
permanance. 

## Generating a DOI with Zenodo

To begin, go to [Zenodo]{https://www.zenodo.org/} and get an account by
clicking the sign up button in the upper right hand corner.  Then click the
'Upload' link at the top of the screen and the green 'New Upload' button.
You'll see a place to drag and drop the files you're going to upload. Then
click the green upload button.  

Next, you'll have to enter the metadata that describes your scholarly work, some of
which will be registered with your DOI.

### Basic Information

First, select the type of object you're uploading.  Is it a publication,
poster, presentation, data set, image, video/audio, software, or lesson?
You can have multiple individual files associated with a Zenodo record, and
you'll want to group them in bunches that other users would want to download
together.  For example, if you have lots of data files from the same experiment
you would want to upload them to one record. If you have presentations on
different topics you would want to upload them to separate
records.      

In most cases you'll want to let Zenodo add the DOI and publication date.  
Next, enter a title, authors, and description.  Make your description detailed
enough so that others can understand the files you're uploading.  It's also
good to enter some keywords to enable discovery.

### Access and Licensing

Zenodo allows your files to be open, embargoed, restricted, or closed.
Embargoed files become public on a selected data.  Access to restricted files
can provided to specified users, and closed files are completely restricted.
Because we're doing open science, select open! 

You should select a standard license for your files.  There is a lot of issues to consider
when selecting a license, and we have an entire
[lesson](https://authorcarpentry.github.io/licensing-cc/) on the topic.  For
data sets a "Creative Commons Zero" license is a good choice.  For
presentations and images a "Creative Commons Attribution 4.0" license is a good
choice.  On Zenodo you sometimes have to type out the entire license name
before it finds it.

### Communities

Zenodo has user-selected communities of records.  These are self-organizing
classifications, and there may or may not be one that matches your work.

### Funding

The funding field in Zenodo is specific to European Union grants (FP7 and
Horizon 2020 programs). If you get funding under these programs your work will
automatically be reported.  Zenodo currently recommends you add additional
funding in the "Additional Notes" field (this is less than optimal).

### Related Identifiers

Related identifiers are a way to connect different works together.  For
example, let's say you have a data set that is associated with a paper.  You
can add the paper DOI to Zenodo as a related identifier with "is
supplemented by this upload" as the description in the second field.

Note: This relation is registered with type "is supplemented by" with DataCite because
all DataCite related identifiers are in referenced to the registered work.

### Contributors and Other Metadata

You can provide some basic descriptions of contributors to a work that are not
authors. Your options are a bit more basic than discussed in the 
[attribution lesson](https://authorcarpentry.github.io/contributor-and-credit/).

There other more specialized metadata categories for References, Subjects, 
and other descriptors.  These may or may not be relevant to your work.

## Finishing up

Once you have your metadata entered, click Save.  Then click Publish to share your record. 
You'll see that Zenodo brings you to the public record page for your work.
Zenodo provides a citation that includes your newly created DOI.  We'll be
using this DOI throughout the rest of the workshop.  

Previous: [Anatomy of a DOI](01-anatomy-doi.html)  Next: [DOI Metadata](03-doi-metadata.html)  
