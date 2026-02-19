
# So the part auf A-H[ao]lodeck was actually supposed to be a joke, but... ❤️⭐️

And then things changed.

> Honey, I accidentially... "AHAlodeck!"

And the path to a quite real holodeck, becomes smoother, the more I test and research and use it myself already.


Simply starting out as `aha.tar.bz2`.
On my drive.
It's a 0-Byte-Files-in-Folder-Ghosttown, yet annoted properly using extended filesystem attributes.

So I unpacked und opened it with `--xattrs` enabled.
And you can browse a well-known, yet foreign (data) file-structure tree, and browse/search/use all its attributes in an order key/value database spirit.

Quite intuitive, and supported back to before 2000s. Officially implemented and stable at least since 2010 (to be on the safe side ;)). The support for xattrs is large enterprise cloud approved and in daily used: To set and manage data-security attributes in data-centers around the world.


## So what is "AHAlotar"?

It's like a very nice, simple holographic-interface unit.
Sounds complicated?

It's as described above:
You end up in a files-in-folders tree-view of a mixed collection of my data.

And you can fully browse it like with a regular music or cataloging application.
Just like that. Key/value filesystem attributes.

Imagine, you browse that holotar like a catalogue of ... music!
And you find something (by metadata or relationships) that you'd like to hear:
So one of the keys has a torrent-magnet link with it: So any holotar-item can immediately be spawned from 0-Byte to full-payload + (more) metadata + hashcode included (as yet-another trusted.xattr).

Awesome!

Imagine a web=file-browser engine that parses your local data, and resolves and handles www-links/URIs/URLs of any kind.

Imagine it, like being able to manifest anything from such ahalotar-catalogue "thin-copy".

That's why I think of it like a hologram:
You get a very tiny unit of it's structure, holding enough information to resolve itself to more detail - if space (and links) allow.

That's it.


## Yeah, but a reeeeeaal "Star Trek - Holodeck(tm)" is like a real world, Dude!

Yes.


## Using AHAlotar as full-duplex control interface over 'data'.

So, follow my trail of thoughts from "ahalotar" for browsing - and ordering - music, to a control interface over that collection.

You'd like to listen to a song, found by browse/searching.

Double-or-right-click it: The aha-engine (=software) supports handling torrent and other links - even pure curl or wget snippets as run-able attributes work fine.

You'd like to "order", select, favorite - simply "do" anything with something you found in the holotar collection data:

> **"Simply add tags"**

Yes.
Add you own.

Depending on who you exchange these holotars, and expect them to work, most holotar-objects (=1 object or a whole tree, same-same) are expected to be "interpreted" in their present context. metadata and policies apply "data-lenses" and permanent-or-ad-hoc transformations (see Chapter: "aha-transX")are performed all the time as normal and expected back-or-foreground processes.

So if you open a holotar in a suitable computing environment context (think: environment-variables, and related data and accessible net-links, plus file-permissions), it should be able to "boot iteself" to some useful manifestation - if at least: a very handy holo-catalogue (.aha) of any data-collection.

Very nice!

Now I've added "download=yes" to some - and then re-sync'd it with the source (yes, works over ssh+rsync): So my "other one" now has a merged attribute-enhanced copy of his version.
(Yes, attrs can be managed by version-control as well. Currently needs some scripting in git, but it's claimed possible - and simply /will be/ once you see how useful this is!

You see how easy and smooth that was?

Once again:


  1. You get a `aha.tar.bz2` file. From somewhere you trust and work on data together with.
  2. You unpack that AHAlotar - or 'holotar' for short.
     You get a familiar files-in-folders 0-byte thin-copy tree.
     You have full and instant access to /all previously embedded or available metadata/ - by xattrs.
  3. You may resolve attribute-links to further meta-or-data content, on demand and interest.
  4. You can simply "undo" (=release) the additionally (temporarily or permanently) fetched data on demand. 
  5. You may "put your wishes or interaction-prompts" into new attributes, or edit existing ones:
     Then re-synchronize (or not), yet use tags like "backup!" to your VIP-stuff, and have your backup application "Look for stuff tagged 'backup!'" - rather than having to re-configuire folders, just to find out, you already have your stuff spread /everyone/ on so many devices and storages. Some of them on shelves... puh...

  6. Fear not! AHAlodeck simply makes you find your stuff.
     Once and for all.
  7. And add "blunt intelligence" to itself by memorizing "your queries and
     your subsequent paths taken" to find what you were looking for in your
     "data pools" from now on: Add textfiles.
  8. Given the xtoolbox (Creators Sir Tómas R. Hak, Kiki P. Gonzales), it's trivial to create a flat csv structure with attributes+filepath: And **extremely** valuable and fast at the same time.
  9. You can now address (=ID) and use as well as share (and improve) on literally any data-object "to your access", by using a ❤️⭐️-mnemonic string.

For example, may I spawn you the first holotar right onto your machine?
REaDY?
SET?

# The first real AHAlotar: Try it for real.

Dare to run this?

> wget aha://⭐️2006-XBloome-legacy❤️

...a few bytes.
So you did? Great!
Wow. Where'd that data come from?
Probably in this case "the internet" - or a "file" right next to this one - or in the $PATH of its environment, and so on... "it depends".

But this works on local files, at it does "in a global cloud" situation.
Same-same.

That ID is resolved, just like all IDs are: Somewhere there are lookup-tables.
"id-to-string=URL", and so on.

Dare to open that present?
Okay, so your name-resolution doesn't "aha://" yet. No problem:

> wget http://arkthis.com/⭐️2006-XBloome-legacy❤️

In this case, that's hardcoded on the first protype index on our AHAlodeck :)
But any URL would work. Resolves recursively until data found.

And in that famous XBloome-Holotar, I've simply added a few links to sites, images, and of course: songs and youtube and other videos and things. Even links to my local drive.
If that file has a ❤️⭐️-ID with it, you can actually resolve it right now, if you like!


## So, now you're on AHAlotar "basic holodeck".

Now, please feel free to use /that very filesystem/ to contain even more metadata:

  * Useful links (Wikipedia, wikidata, n-best search results on platform x,y,z, etc...)
  * A preview thumbnail image
  * A preview audiovisual snippet? (Yes, that's possible too!)
  * Use RDF where useful and possible, both: key and value. Have fun!.
  * Much of this can happen automatically using a one-time on-demand import script:
    Mostly based on popular metadata all-star extraction tools: exiftool, mediainfo, uvm.

You can attach any metadata information currently stored elsewhere: from databases "about this object", to textfiles, spreadsheets (ods, xlsx, csv), even store the SQL-table information directly. All perfectly possible and inviting to do so.


# Where's the gain? Where's the catch?


## GAIN = it's awesome to "find and link stuff. Anything really."

Easy: Gain = you now find all your files, regardless of data-format in a common interface - and can related anything to anything - and use that to interact with your data, in ways you previously would have required specialized asset-management tools.

Now, those "DAM tools" break down into data-managing environments: like openRefine, Obsidian, Wikibase, SPARQL + JSON(-LD), jq, etc.

Beautiful.
And highly interoperably by design.

Very useful for anyone dealing with digital data collections of metadata+payload over hundreds, thousands or more "assets", including copies and rights, and heritage and science and personal and private - META=DATA in general these days.

Got Terabyte?
Got enough... RAM/Tool/Budget?


## catch?

I can't find one so far. To be honest. This is what still nags me a bit.
I find no flaw.
Now I feel like sounding like a cars-salesman (which I actually have /NEVER MET A SINGLE ONE/ like the ones depicted on TV - or Monkey Island ;) ) - but I feel exactly like one of those /to you/.

Okay, there are some things I may be "worried" about.

Here's what I'd be interested to see for real and how it performs and behaves:

  1. The perceived data-quality over time.
  2. The practically useful data-quality over time.
  3. The issue with "too many copies of same-same-but-different" objects
  4. The legend of the DATASWAMP monster!
  5. Performance in general on differently-sized collections with different
    "heavy-or-lightness" on metadata. Payload manifested by torrent magnet
    networks.
  6. Handling synchronizity and "update-enough-ness" of relevant caches - and if "reboot-context-load" is enough, etc.

Working with attributes should actually create very little "data traffic" and filesystem changes in general, as the "payload" (=the heavy stuff) stays in place most of the time. Only fetched or loaded if actually requested for use.


# So what did you get out of this?

> wget aha://⭐️2006-XBloome-legacy❤️

  * Attributes, linking to online stuff from the band "XBloome".
  * Including outdated, yet originally valid website links and other URLs (=web-history)
  * Links to their music
  * Links to tutorials, information, interviews and HowTos from XBloome on "how to record-mix-master-publish your own" music and other stuff.
  * Links to tool-templates for CD production (Scribus, Gimp, etc)
  * Other useful "FOSS tool plugins or scripts" to work with musical releases, including lable-registration, - even contract templates.

Wow! Quite a box of useful stuff if you're interested in the electronic-mixed-style, like XBloome played.


If you get more curiuos and would like to gain access to rehearsal sessions, simply add "a well-known easter-egg" to the random-part of it's CFID aha-id (❤️⭐️)

> wget aha://⭐️2006-XBloome-legacy-rehearsal❤️

...and off you go!
Loads of never-published raw recordings.

Fell in love with their style?
Would like to add or create or modify your own?
Great! Feel free to browse this box of inspiring art-works truly multi-medial and collaborative. Imagine this works greatly on all CC-and-similar licensed "link and data collections". Any of which can instantly be stored, and used and exchanged as ahalotar.

And once used, the user-and-commandline-interfaces for "get-by-❤️⭐️" environments.
It's like sitting in a constant "redis-filled-pool" of "your and others' stuff".

All managed and stored well.
Entrusted as you like and will.


So you literally fell in love in falling in love with music again, and would love to have a copy of their individual recording tracks, or original sources of artwork, etc:

> wget aha://⭐️2006-XBloome-legacy.free❤️
> wget aha://⭐️2006-XBloome-legacy.love❤️
> wget aha://⭐️2006-XBloome-legacy.peace❤️
> wget aha://⭐️2006-XBloome-legacy.freedom❤️
> wget aha://⭐️2006-XBloome-legacy.tracks❤️
> wget aha://⭐️2006-XBloome-legacy.artwork❤️

You'll see this like this in your filemanager:

⭐️\
  |- 2006\
     |- XBloome\
        |- legacy.free❤️
           love❤️
           peace❤️
           freedom❤️
        |- tracks❤️
        |- artwork❤️

How does that look?
Realize how "legacy" has "love peace freedom" as alias? they simply point to the same "data".

If this is how accessing a holotar for the first time, on a non-optimized environment for that, imagine what's possible, if ❤️⭐️ IDs became popular. I've ❤️⭐️-my-data collections already. I've even written the script to do that myself. You can either you mine, or roll your own. It's simple:


# AHA-IDs: Collision Friendly IDentifiers (CFIDs)

This is what turns the data-lake to some kind of auto-structuring "relationship-goo", which has the nature of providing "interesting and fruitful collisions", rather than id-collision being a bad thing.

It can even go so far, as to be preferred to include and merge "other attributes" on objects whose IDs collide - or "match close enough" by policy or context. There's even the option for data-attributes to "rub off" in a good way:

I'm serious! :)
Here's "metadata rubbing off":

  * You have a folder called "XBloome".
    Common inheritance of attributes is supported:
    That folder has "common" attributes, related to "XBloome", which are
    automatically present on any fs-object "in that folder".
    Such as: dc:creator, dc:date, web-links, etc.

  * Now, imagine this inheritance abiding to some patterns:
    * The copied/created timestamp is set.
    * time-to-rub-off (TTR) either on each value or as common-for-context setting.
      time in "some time" (seconds, etc).
    * a computing environment refreshing those "TTR" values. Just like
      garbage-collection taking care of "TTLs" running 0.

  * So :The longer any new file (object) would stay "in" such a folder,
    the more attributes will be "copied over".

  * Imagine computing being under your control again.
    Because otherwise, the features I'm offering you here will feel quite creepy in the wrong hands.
    However, I do believe any experienced linux-sysadmin-devops are already
    well-aware of this and using ZFS anyways.

  * And you could configure this behavior by arbitrary patterns (or paths) of your data.
    Because "the path" was just /one way/ of getting there.


## Rubbing off a codec!

So imagine, you receive a new media-file from somewhere!
And your system doesn't know that file-format:
It contains links - or even code - or even binary - to "play" fine.
Imagine ArchLinux magic-by-text to build required dependencies of anything out of thin air!

And since the "rubbed-off-transferred" data is stored in attributes (not IN the file), it's not limited to 1 file-format or data layout.

You can literally have "your files learn codecs from around them":

Imagine you have a 0-Byte Object.
Tag it "movie", give it a title, and throw it with a bunch of media files.

The media files got "pimped up by encoding/decoding metadata attributes and Makefiles" - or simply "a link to videolan.org". This already increased their global instant-playability by 1000%.

Just add metadata ;)
And "A HAlodeck around" it.


## *ähem* - Wo war denn bitte jetzt VR und so?

Okay, given this engine and the ability and willingness to think in related-data-objects, calling it each other by ❤️⭐️ - and that just works.

Simply import the actual file-format and file-system structures with their current naming: blender-by-blender project: and relate them to their rendered outputs.

"Let IA watch those movies and learn their blender project 'language' natively"

Given that your blender - and all related assets (!) loaded "once" by importing a blender project: Each object created in memory - or relevant for the task - is given a ❤️⭐️, 


# More or less memory required?

The CFIDs are taking up a few more megabytes in each copy. True.
I should do the math, giving some examples for "how many MBs are how many pages of text".

Because that's what will also increase, when resolving file-format binary headers to xattrs.

However: We're still talking METAdata: so hundreds of MBs are already quite much.

And AHAldeck will and shall make use of plenty of cache-space for brilliant operations, but also work genuinely on lower hardware. Just slower. Rest is exactly fully-interoperable.


## Simply honor xattrs, and supply nice handling of them.

Your operating systems and computing environments will be configured to expect and respect those key/value tags of any form. And do its best to make sense (in your interest = policy & configuration & implementation) of choices.

Don't be greedy with tags.
Your system would be very capable of handling the same amount of data in /their/ databases.
No bad intention: Even my very beloved favorite "Clementine" music application uses "its own" SQLite. Fine.

Just not necessary anymore:
Everyone meets on the filesystem.
And in a computing environment where attributes are respected and supported well.
Actually, it's already natively built into today's alreay legacy high-quality filesystems like ZFS, EXT4, (`*`), HFS+, APFS, btrfs, POSIX, ...

So chances are quite high, that if you're storing stuff on a GNU/Linux-powered, POSIX-compliant environment: you're already owning your AHAlodeck basic hardware.

Actually, AHAlodeck is quite nicer on resources, compared to all things currently running-parallel doing same-same-own-database handling of some sorts: Down to CSV and SQLite. Which are both brilliant data-exchange and handling formats, btw! Thanks to everyone who made it possible! ❤️⭐️


So what are the next steps for creating and "browsing" AHAlotars?
This was a regular files-in-folders interface with calls to browsers and other applications. Already working quite swell actually! Most applications load-by-URL these days, anyways ;)







