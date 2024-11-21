# FAQs

  * **xattrs, EAs, XAs, resource forks, named resources: Eh? What now?**  

    Yes and all of that.  I'll try to stick to "xattrs" and "XAs" for when I
mean "extended file attributes in general".  I use "XA" as "I can store
key/value data with an fs-object" (FileSystem-Object).  Like YUV and YCbCr,
etc...  I prefer using them term `xattr` (unless I'm too lazy to type, then
`XA`).  Also because to give all Linux/POSIX developers credit for taking
interoperability seriously. Respect and Thanks.

  * **Are XAs reliable?**  

    I'm pretty sure they are.

    As long as you stay on the same filesystem/partition.  However: It's still
an officially stable feature of many existing, mainstream and server systems.
And used for dead-serious security (SE-Linux, etc).

  * **Will XAs get lost on their way?**

    Depends. If you take care, probably not.  And if there are data-paths or
    environments where xattrs are not expected-or-known to pass intact, one can
    simply choose to do the same workaround we do today: make a plain text/binary
    backup of those attributes (eg by tar-ing just the XAs).  And re-import once
    the data has reached a target-FS which supports xattrs.

    Caution must be paid to the total size of the key+value data - and the limits
    of the filesystems that data is intended to travel. For now I highly recommend
    having a (text-)backup of XAs you receive or set. If you expect to keep them
    (longer).

    Text-encoding issues (as known with filenames) should not be an issue, as
    xattrs are treated as "plain Bytes" by the filesystems. Application /may/
    mis-interpret or change those attribute's encoding. However, this is quite
    unlikely.


  * **Why aren't XAs the standard, if they're so awesome?**  

    Good question. I don't know.

    From a professional point of view, I believe xattrs were simply way before
    their time.

    And the fact that *embedded* metadata and files-in-folders with
    spreadsheets and DBs - were just good enough. Now data-management has become
    expensive and very staff-and-resource-hungry. Especially with IT skills.

    With today's hardware and memory sizes - available on the regular user's
    desktop/notebook - even mobile equipment: enough to unify all separated
    metadata-handling-apps and formats into simply using extended attributes.

    It's what they were designed and built for.


  * **Can I store all my meta/data in xattrs?**  

    No. Maybe. Depends.  On the actual filesystem/environments you're using.

    The type of (meta)data you store is irrelevant.  The filesystem keeps
    xattrs as "Bytes".  Up to the reader to interpret. Awesome. Bit-safe. Any
    char/data-encoding possible.

    Some tools even support preview-images as attributes (macOS? Haiku BeFS?)

    At least up to 4 kBytes of key+value total, you're on the safe-side on any
    FS that supports XAs.  I haven't run tests yet, but docs and online discussions
    say that some may store up to 64kB easily - and spawn related inodes if the
    attribute-data size gets beyond what fits in the metadata-block of a
    file/folder's inode.

    Any limitation of size is merely a design decision.  This can be
    changed/improved if using xattrs shows successful.

    For now, it's enough to keep all my music- and camera-tags as xattrs.
    Awesome to work with.

  * **Can I use XAs with "tools/OS" of my choice?**

    Very probably: YES!  That's the beauty of XAs:

  * **What about performance?**  

    I'm comparing xattrs to the status quo of personal and professional
    metadata-handling and storage.  I'm **not worried** about performance (yet),
    but I haven't done hardcore testing with larger datasets yet.

    In a nutshell:

    * All music/photo tagging applications have some kind of database (like
      sqlite)
    * So the metadata is stored twice: in the file (embedded) and "in" the
      application's internal storage.
    * Another time (maybe), if one has a desktop-search indexer running.
      Pointing to the same collections.
    * Larger collections have catalog and task-management systems to handle
      data processing and access.
    * Converting applications to use the filesystem as go-to database/index
      instead, will actually reduce storage/memory/process needs, compared to
      now.
    * Most "larger" collections already require cache/indexer networks setup to
      actually work with their data.
    * Using xattrs would be way lighter, as common functionalities could be
      streamlined - by libraries and OS environments.
    * The overhead of "yet-another" parser for each file-format, just to access
      its metadata: obsolete.
    * This means less code to load, run, maintain, download, consider, etc.

    I think this speaks for good performance, compared to now? :)


  * **What about (additional) data-size?**  

    As mentioned in "performance" above, the data is currently doubled: because
    of keeping the embedded originals for an expectedly long period from now.
    Adding indexing, makes a 3rd copy.

    We are still talking about mostly-text "metadata" for starters.
    Considering that a whole wikidata dump as of today is around 130 GB JSON for
    its entities - and I have an affordable server with 128 GB RAM sitting on a
    desk behind me: I'm not yet worried about data-size either.

    And even if we start to auto-thumbnail everything as attribute: Those
    thumbnails are created and stored already. And when you copy your files - the
    receiver system does it anew.

    I am **not worried** about additional data-size, compared to now.


  * **You mentioned de-embedding technical file-headers?**

    Indeed.

    Imagine any technical-binary file-format-specific data-header
    would simply be translated (once) from existing file-formats to a copy as
    attrs? Simply right-click-anything to see what it is.  And editing *that*
    metadata would actually change the file like you've used a hex-editor now.
    Just plaintext and numbers.


  * **You also mentioned resolving container formats?**

    Yes.  IF you have followed the idea of seriously relying on xattrs to work
    and be present - just like long-filenames with Unicode characters today: Why do
    you need/want a container format?

    Once, using xattrs is more common, imagine your video-files being pointers
    to related audio/video/metadata files (Objects)?  Why not?  Resolving xattrs is
    trivial, I've made a post to ffmpeg-user about that idea.


  * **They feel so obscure. Almost hidden. Feels odd and scary.**  

    True. But not necessary.

    Imagine xattrs being the normal go-to thing you do when you want to know
    anything about "a file" (Data Object).  Then, seeing its security-attributes
    (like macOS quarantine/download-flags).  We're just not used (and lacking UIs)
    to handle XAs nicely.


  * **Can I create an attribute-only copy of a file?**

    Yes.
    This "thin copy" is very useful for transferring or securing metadata stored as XAs.
    The command on linux (and possibly MacOS too) is:

    `cp --attributes-only --preserve=all "SOURCE" "TARGET"`

    The result (`TARGET`) is a 0-Byte (no payload) copy of `SOURCE`, including
    all supported filesystem attributes.

