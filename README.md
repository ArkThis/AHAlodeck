# AHAlodeck

Welcome. :)

Here's some links for direct, hands-on stuff:

  * [FAQs regarding extended attributes (xattrs) on the filesystem (Linux/Mac/Win)](doc/xattr_faq.md)
  * [Project Proposal Draft](https://github.com/ArkThis/AHAlodeck/blob/main/doc/AHA-Proposal.md)
  * [Proof-of-Concept (PoC) Prototype: MERCS](https://github.com/pjotrek-b/mercs/):
    A plain simple GUI for editing extended file-system attributes `xattrs` on Mac/Linux (Python3/Qt6)
  * [json2xattr.py](https://github.com/pjotrek-b/mercs/tree/main/helpers):
    A powerful "helper" commandline (CLI) program to copy from any JSON key/value source to `xattrs`.
    Combined with [exiftool](https://exiftool.org/), it already works great to de-embed most metadata of any file-format supported by `exiftool`.
    (Tested on 15.000 Object typical music collection: 60 MB key/value => 1.2 MB tar.bz2 **"instant catalog"**
  * [Recoll](https://www.recoll.org/):
    Brilliant desktop-search FOSS and cross-platform app (support it!) that supports `xattrs` (since ~2015, already).
  * [Infos on 'Config to full-text index all extended file attributes (xattrs)'](https://framagit.org/medoc92/recoll/-/issues/281):
    This is an ticket I raised on Recoll's git, ending up containing working-config examples for using xattrs for daily use.

  * More FAQs about Object Storage, Schema-evolution, etc. shall follow.


--------------------

# TL;DR:

> Just imagine being able to "tag" (somekey=somevalue) any file and folder:
> **Right-Click-Edit-Metadata.**
> On anything being "digital data".

Across all platforms, applications, file-formats, etc.
If this sounds interesting to you, enjoy reading on! 🌻️

--------------------


# Intro: AHAlodeck - "A Holodeck by August".

Based on years of practical experience in the field of [GLAM](https://en.wikipedia.org/wiki/GLAM_(cultural_heritage)) (Galleries, Libraries, Archives and Museums), I have come up with the idea to combine storage+catalog - in the filesystem.

Working title became: "AHAlodeck".

Here we're a distributed group of "GLAM-professionals", working on building a very simple, yet powerful environment that can digest "Meta+Data Objects" in clever ways.
Based on already existing FOSS components that we orchestrate to each other.

**We simply combine existing, stable technologies (like [xattrs](https://github.com/ArkThis/AHAlodeck/blob/main/doc/xattr_faq.md)) using that filesystem directly as database.**

> And it's as accessible and easy as "simply putting a letter in a filename/path"


The following image is a screenshot of a prototype setup:

It shows a 0-Byte "file" being tagged to contain references to "other Objects".
And that 0-Byte file having a title itself: Fully performing as a database entry.


![Using xattrs (ext4) Xubuntu: out-of-the-box.](res/0byte-db_entry.png)

--------------------------------

AHAlodeck is *not only* about re-introducing extended file attributes.

It starts with using `xattrs`, and then going towards a filesystem which graph-node capabilities and more, by using ObjectStorage features.

> If I'm correct, then I may introduce a change for anyone dealing with digital data, **comparable to going beyond 8.3 uppercase-only ASCII characters in a filename (1995), to Object Oriented programming and responsive design**: Using common, existing filesystem features. 😄️

It is incredibly simple and feels very useful already in early prototype components.

Yes, you can simply right-click-edit-metadata on /anything/ from now on.
With any tool that supports "the new long filenames". 💾️



![Prototype Screenshot](res/pyQtThunar-rightclickedit-metadata.png)


What I am suggesting is to use existing #FOSS-licensed technologies designed for storing and managing modern (even big) data. And really letting go of files-in-folders with excel sheets and incompatible databases and embedded metadata to a data-design and handling, making use of proper Object Storage environment's capabilities.

  * Simply, putting metadata with the data: Where it belongs.
  * And draw relationships right with others of those same "Meta+Data Objects".
  * And support (de)referencing any kind of "link" information.

Even supporting torrent magnet-links for options like having light-or-heavy Data Object manifestations.
On the fly. ;)



## More?

Welcome.

This is ongoing research-and-development.

In fact, we're mainly starting with using xattrs and plan to patch existing code to provide on-board features for working with seriously-used "xattrs" - and going Object Storage, Swift, Apache Iceberg, Sparql, Recoll, etc.



# Why?

Because the current way meta+data is handled every day has become a bit challenging and demanding.
And I'd like to improve that. For myself if noone else.

If you have good answers to the questions asked in the following image, please let us know:

![`gthumb` handling image metadata.](res/gthumb_metadata_questions.png)

If your job is to care-or-know where which of what metadata goes with what "Object" where - and why: And where it is all stored and accessed digitally, you've come to the right place.

This is what we're trying to finally make it fun again.

🌈️🌟️🦄️


Peter B.
(ArkThis AV-RD)
