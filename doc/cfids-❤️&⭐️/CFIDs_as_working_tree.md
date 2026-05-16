# Using CFID Files-in-Folder (FinF) trees as working copy

## Reworking, renaming, relocating files. Easily.

Imagine the following setup:

  1. You're asked to work on existing digital collection data.
     This may be heritage institution data, or something like your personal photo or music file collections.

  2. The original collection has hundreds of GBs - or even several TBs - or larger.

  3. You create a "Holodex": A thin-copy of your original data as 0-Byte FinF-tree: files in the original folder structure - with key/value metadata as filesystem attributes.

  4. Tar and bzip2 that Holodex and you'll probably get away with a few (hundred) MBs in a single file.

  5. Transfer that to your local AHA-capable storage, and work with the data.

You can now re-arrange, rename, etc all the datas, as you see fit.
You can browse/search/map-and-transform them by all metadata that comes with them.
(Most previously embedded metadata should work)


## How to re-apply the changes onto the original?

Here's where it gets really beautiful.

  1. You take a proper xant for that.

  2. That Ant requires 2 parameters.
     a. The Original
     b. The (modified) Holodex copy


How does that XAnt work?

  1. The Holodexer auto-generated (or copied existing) CFIDs from the Original and wrote them in the Holodex/Holotar.

  2. Therefore any file or folder can uniquely be referenced by ID.

  3. Since the filesystem (FS) supports snapshots (as a proper Copy-on-Write (CoW) FS), you can always revert back to the Original anyways.
     Since we're just editing filesystem *metadata*, the snapshot overhead/size should stay relatively "small" compared to the actual payload data in files.

  4. xapply the modified Holodex Copy onto the Original:
     In order to get the matching CFIDs back onto the original Files-in-Foldes (FinF) data

  5. Create another thin-copy (or hash-tree in memory?) - of the COPY - as follows:
     a. Store the current (modified) path/filename as xattr.
     b. Rename the "old" (=original) path/filename from 'filename' to 'filename.1' (so it's not the default choice anymore, but provenance metadata).
     a. Split the CFID in human-digestable-yet-not-more-than-n-chars substrings, and use them as subfolders.
     b. Use the CFID as-is as filename.
     c. For data-efficiency, one may omit the heart-n-star emoji-glyph-enclosure on that level.

  6. If CFID-collisions should happen in that step: great!
     a. Merge-conflict-handle them.
        Like you would with source-code.
     b. If you use `fingerprint=hash.md5` in holodexer.ini, different payload (=file content) will have different $RANDOM parts, therefore only colliding if they /are/ the same file.
     (Hash collisions are expected to be insignificantly low, or another hash algorithm can be used for fingerprinting, if one wants to)
     c. Add random chars at the end of the CFID, if you encounter unwanted collisions, until they are "unique enough".


  7. Now, that hash-tree (in RAM or FS) can easily be used to quickly lookup "path/filename" from the files-in-folders (FinF) object - by ID. By its CFID.
     Even both: original and new path/filename!
     This allows easy and clear access to knowing which file/folder (FinF) object to move to its new destination and naming.

This allows working with arbitrary-large collections even locally - on a desktop/notebook computer. Great for dealing with remote collections of AV or film material (which are quite large in data-size, yet nice-to-handle their metadata).
