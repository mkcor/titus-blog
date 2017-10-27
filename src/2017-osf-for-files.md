Title: Using the Open Science Framework to share files, for Science.
Date: 2017-09-21
Category: science
Tags: osf,osfclient
Slug: 2017-osf-for-files
Authors: C. Titus Brown
Summary: Share files for fun and nonprofit.

Sharing files in the 100 MB-5 GB range has been a perennial problem for my lab - we want to post them someplace central, perhaps publicly or perhaps privately, and we have several use cases that complicate things:

* sometimes we need to share files with collaborators who are not so command-line savvy, so an easy-to-use Web interface is important;
* other times we want to provide them as part of documentation or protocols (e.g. [see my recent blog post](http://ivory.idyll.org/blog/2017-classify-genome-bins-with-custom-db-part-2.html)), and provide simple download links that can be used with `curl` or `wget`;
* when we're doing benchmarking, it's nice to be able to save the input and output files somewhere, but here we want to be able to use the command line to save (and sometimes to retrieve) the files to/from servers;
* occasionally we need to share a collection of medium-sized files with dozens or hundreds of people for a workshop or a course, and it's nice to have a high performance always-up site for that purpose;
* if we publish something, we'd like a location that we can "freeze" into an archive;

and of course it'd be nice to have a single system that does all of this!

Over the past decade we've used a variety of systems (figshare, AWS S3, Dropbox, mega.nz, Zenodo) and ignored a number of other systems (Box, anyone?), but none of them have really met our needs. GitHub is the closest, but GitHub itself is too restrictive with file sizes, and Git LFS was frustratingly bad the one time we engaged closely with it.

But now we have a solution that has been working out pretty well!

Enter the [Open Science Framework, osf.io](http://osf.io), which is a ...well, it's complicated, but it's a site that brings together some project management tools with user accounts and data storage.

I first encountered OSF in 2015, when we visited [the Center for Open Science](http://cos.io) as part of the [Open Source/Open Science meeting](http://ivory.idyll.org/blog/2015-osos-meeting.html). COS does many things, including running [various reproducibility projects](https://en.wikipedia.org/wiki/Reproducibility_Project), being engaged with [research study preregistration](https://cos.io/prereg/) and hosting [a number of preprint sites](https://osf.io/preprints/).  osf.io underpins many of these efforts and is an [open source](https://github.com/CenterForOpenScience/osf.io/) platform that is under continued development. They are serious about their software engineering, in it for the long run, and to the best of my understanding simply want to enable #openscience.

The osf.io site addresses essentially all of our use cases above:

* it supports both public and private projects;
* it has a simple and reasonably robust permissions model;
* it is quite usable via the Web interface;
* with only [a little bit of trouble](https://twitter.com/danudwary/status/907628615101169664) you can get download URLs for individual files;
* we (by which I mean mostly [Tim Head](https://twitter.com/betatim)) have a ~beta version of a command line utility for interacting with the OSF storage system, called [osfclient](https://osfclient.readthedocs.io/en/stable/), which [actually just works](https://twitter.com/ctitusbrown/status/907636578897477634);
* it's free! and will store individual files up to 5 GB, with no project limit;
* they support "registering" projects which freezes your project at a particular point in time and gives you an archival location for that version (think GitHub + Zenodo style DOI generation);
* they have a sustainability fund that guarantees that even if COS itself shuts down, the osf.io site will continue serving files for an extended period of time (last time I checked, it was 50 years);
* you can even do things like host UCSC genome tracks on osf.io (and when you can't, because of bugs, [they are really responsive](https://github.com/CenterForOpenScience/osf.io/issues/7020#issuecomment-313495034) and fix things quickly!)

and, coolest of all, they have "community advocates" like Natalie Meyers who are [actively looking for use cases to support](https://twitter.com/nkmeyers/status/885898300976766977), which is kind of how we got involved with them.

So... give it a try!

In the past six months, we've used osf.io for --

* [posting ancillary files for a publication](https://osf.io/k8pr5/);
* [providing files for blog posts](https://osf.io/9876b/);
* [caching large files for sharing with the community](https://osf.io/rjp38/);
* [storing data generated by an annual experimental course](https://osf.io/9bytm/);
* [posting talks, presentations, and posters](https://osf.io/w7m2d/);
* hosting internal "private" projects;

and more.

There's a bunch more things that osf.io can in theory do that I haven't explored, but, at least for now, it's meeting our file redistribution and project file sharing needs quite handily.

Where next? I'd suggest trying it out; it only takes about 5 minutes to figure out most of the basic stuff. You can ask them questions on Twitter at [@OSFramework](http://twitter.com/OSFramework) and there are [FAQs](http://help.osf.io/m/faqs/) and [Guides](http://help.osf.io/) ready to hand.

--titus

p.s. I've had extended conversations with them about whether they really want the genomics community descending upon them. They said "sure!" So, you know, ...go for it. :)