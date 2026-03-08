# Collision Friendly Identifiers

## Short update: Supports emojis

Current syntax proposal for this kind of identifier, consisting of 3 parts:

> `⭐️$TIMESTAMP-$CONTEXT-$RANDOM❤️`

* `$TIMESTAMP` = kind-of-iso8601 date/time information.
* `$CONTEXT` = Any string you'd refer to like an "identifying title".
* `$RANDOM` = A random-or-pattern sequence of characters.

Each part may be tuned to more-or-less precision.

**NOTE: The rest of this article is slightly outdated (Syntax), but the basic idea described herein is still valid**

## Abstract

Reconsidering the "uniqueness" of a digital identifier to a point where a "pattern collision" limits the number of individual Objects that could theoretically co-exist at the same time. On purpose.

To allow "intended" collisions of IDs.

A variable uniqueness per ID, so to say.

Including the fact that actual collision sometimes shall happen on purpose, triggering a policy-rule based merge situation. Yet, when and how often for which "kind of Data Object" this shall happen can also be configured easily, and individually.

With policy rules - or simple UIs for the ID's components.

> **The collision events are desired triggers for (transformation-)actions on Meta/Data in Objects.**

Such as:

  * auto-merge / auto-relate matching Data Objects.
  * and cluster similar ones.
  * all by a simply plaintext, human-friendly ID.


# What does it look like?

The format is this:

`$timestamp/$title/$random` (TTR)

The total (maximum) length of a CFID is ...?
Good question. 4096?
Consider: Youtube IDs are only short ASCII strings.

Here are some examples:

  1. `20250117T001337/CFID_Article/72hcgyWs!d`
  2. `2006/Artist/XBloome`
  3. `2006/Band/XBloome`
  4. `yyyy-yyyy/Paradise_Revolution_1`
  5. `20250117T00133765/auto_demon_process_XY/72hcgyWs!d`


Similar, yet slightly mismatching dates/titles will collide and auto-cluster by their patterns.

Over time, if one desires, it becomes trivial to "clean up" (=consolidate) if you wish unwanted leftover "typos" in IDs.
As well as easily exchange "transformer" mapping Objects which contain "in=out" lookup-tables of key-to-key to translate between sources and converge common-enough IDs (with n-to-1 key-mappings).

One may simply provide with a "grouping" Object, the above list of 5 entries as keys.
And give them "target" values to map (or not) to.

There is no more coding needed to perform metadata operations using such Transfomer-Objects (like LUTs).
You simply load-and-apply "such a transformer-Object" selected in your file-manger.


# Details on the ID components

A CFID consists of 3 parts/components:

`$timestamp/$title/$random` (TTR)


## Timestamp

A timestamp in condensed ISO8601-inspired form.
From "fuzzy-year/date" down to nanoseconds (10^-9) precision.

This can be configured per Object (manually), or applied semi-automatically using profiles and presets.

This is especially useful when annotating entities, such as Agents for example:
When creating a database object for an artist called "XBloome", having a common rule to "use the year of origin" of that band/artist -one may get a CFID like `2006/XBloome`

Individuals, not knowing of each other, annotating data sets with "popular entities", will come up with these very-hopefully-colliding IDs - because they /mean/ the same thing.
Quite possibly.

More on collision-handling (usually merge after a diff-check) later in this article.

If you want to write an article about XBloome, you may also want your article to have a short (=memorable) ID, so people can easily look it up.

What about: `20250103T233800/The_great_article_about_XBloome`

Globally: How likely is it, that someone will $label their "other" (=colliding) object identically, at the same second?
And if it does: Maybe you two should talk. That's destiny then.


## Title

Any human-readable text giving a short context "hint".
Treat it a bit like "the good old filename".

I would like to support full-unicode in the specs, unless there's a good reason not to?
Anyways, this information is expected to be easily available at all times - either asking the user in the UI when opening an application or task or action within, or auto-generating one, based on config, etc.

Anyway, there's still the $random part at the end - which removes the burden of uniqueness from the $title.
So you can keep it short and simple.

One thing: NO SPACES or whitespace chars allowed.

And please: don't abuse it as metadata freetext option (like filenames/folders).
Metadata now has its own and right place: filesystem extended attributes.

It's okay. You can trust them.
Stable at least since 2010 already, and used for serious cyber-security use-cases all around the world.
It's okay. You can trust them too now.

Keep the title short.
$timestamp + $random is pretty good entropy for human-made objects.



## Random

This is an arbitrarily long string of random characters.
Its presence in the CFID completely optional per Object.

It can also be used as a human-override "joker field", as it may at least contain ASCII.

Use it wisely.
Mainly for entropy.

Characterset is limited. Length from 0 - 512 (?) Bytes (or 4kB? or more?)
Inspired by Youtube IDs to be honest.

Considering that the rather short string-ID of Youtube seems sufficient to hold "the world's AV collection in total" blows my mind - and makes me assume: **$random string is sufficient in itself as ID for human-made collections.**
(Maybe keep this limit as a value treated to maybe-increase-in-the-future in your code and configs)

Sufficient = unique-enough in a given context.

  * Q: Is it necessary to constrict the string-length?
  * A: For embedded it might be wise.

One thing: NO SPACES or whitespace chars allowed. Please.



# Introduction

Imagine: You catalog a band named "XBloome" - and my friend also did that - in his local collection.
We're pretty sure talking about the same artist, therefore we intentionally encourage our Objects to be found together on the same storage "realm" one day - colliding.

Merging or selecting yours/theirs.
As you like.
As your system preferences are set.

Catalog metadata entries are stored as Data Objects, with IDs like that would auto-cluster similar "intentions" of Object copies. Auto-generating 1 new out of 2 previous versions (merge xattrs).

If desired, version-control could keep track of all previous data-layouts (including xattrs).

Simply including one aspect of `data-aging` by simple and readable collision-friendly IDs.
:D


## Why not UUIDs?

  * I don't like them.
  * I find them unpractical and uncomfortable to work with. Seriously. Sorry.
  * I find them **very useful** and necessary though at the same time. (brilliant idea!)
  * I prefer technology that is designed with actual people in mind.
  * I prefer things I like to use myself.
  * I feel my brain twists when I try to memorize/use uuids. Exhausting.

Try generating a few UUIDs to get a feeling for the readability of them:

`$ uuidgen -t -r`

Or:

`for i in $(seq 10); do uuidgen -t -r; done`

To get a bunch of them. Including on timestamp and random as input.
I personally find them very hard to read, memorize and work with in general.
They're like hurting my pattern-loving brain-nerves. QR codes alike.

Looks like this:

```
4fab499b-b42f-4fdf-a069-7dc4304510ea
2d3769c3-c31f-4729-8b3c-8b7ec4e8d4f2
0e9e8372-0679-44a7-8db7-6c5fe80451cf
1541e700-4720-4291-9a05-6a624fa8fccd
c764fe69-2bd5-4dde-a623-c14f85c7afba
0b671a7c-c102-4afd-86a6-a9e5afc7cc14
3fd9b307-6422-4b18-ab0a-5082670114d5
90d78a7c-87ac-4611-a274-fad8451b7baf
a622e22b-3183-43f7-af09-8e3a0d0b70e8
f39ac3f6-c02e-457b-a091-165ac862c12d
```

😕️


# I suggest a different, more inviting syntax for `unique-enough` IDs


## Option 1:

I really imagine the following ID syntax as replacement option for UUIDs:

> **Syntax: [🌟️]$timestamp/$title/$random]**

Yes, the 🌟️ is mandatory and required by standards definitions :)
However, /only/ the star is Unicode. The rest shall be 7-bit ASCII only.
This makes it embedded-compatible, where the star-emoji can be hard-coded somehow easily.

Why the star?

In order to be *sure* that full unicode support is given on all implementations, this token must render and behave correctly. If it does, it means that any meta-and-data field is bit-proof and unicode-capable.
Seamlessly.

And if you don't see a `🌟️` - something may be odd with your setup, so you can check.

This is the most original version of CFIDs I've been using/testing so far.
Considering embedded devices, means to me, allowing to have tools at hand for proper analyzing of the low-level structure. So I could attach something into a LAN line - and see my ObjectIDs of my data on an LCD screen or similar low-tech.

It also keeps an auto reality-check on computing resources and style, when checking "Can I Arduino that?"


## Option 2:

> **Syntax: [🌟️]$timestamp/$title/$creator/$random]**

Where `CREATOR` is intended like [DublinCore `Creator`](https://www.dublincore.org/specifications/dublin-core/dcmi-terms/elements11/creator/) - but can be any pseudonym-nickname-whatever string the user prefers and has set.

This is the most recent version I'm considering at the moment.

This is actually technically a hack "with $random" being "$creator/$random" - as $creator is technically just "yet another random string" - including a slash.

Go gentle with thiw knowledge and hack.
It may help some semi-manual self-structuring IDs of related information.
However, neither $title nor $random shall ever be overloaded like filenames are now.
Enjoy relying on seamless support of xattrs and Objects.

Another option would be to use `$COUNTRY_ISO_ID` instead of `$creator`.
Use it wisely, and have a good reason /why not/ to put $country in xattrs?

Anyways: The $random part is your powerful $joker field.


## Challenge Accepted

  * Unique-enough?
  * Acceptable uniqueness?
  * Friendly collisions?

I believe this to work and be useful.

I do invite you to challenge the collision-chances, given the fact that Data Objects are created for a reason (=context = $label)- and at a certain date/time.

So what are the chances of 2 individuals choosing the same, identical `title` at the very nanosecond `timestamp`, being given a matching random character sequence of random-length (up to max. chars)?


I am considering this ID syntax for an Object Storage based `Object storage/reference/linking engine`.
Considering both: small and local, yet also distributed, super large scale data collections by design.

A Data Object can literally be anything you'd now be able to conceive - and use - as a `file in a folder`. Or simply "something data digital" you'd like to do something with right now - and maybe later (find it) again.

Giving them auto-generated IDs with the above syntax, would introduce a design-limitation for "noise" (over-creation of Objects) - due to limiting the address space on purpose. While at the same time, possibly auto-annotating (policy/rule based configurable) any data collection adhering to CFIDs in their "storage".


## Collide on purpose?

  * Yes!
  * Absolutely.
  * On purpose, but *not by accident or error*.
  * And: Have mismatch-score /before/ merge.
  * In case of question: Ask the user. It won't happen a lot.
  * And if it does (annoyingly): Reconsider $random and larger $timecode.

Imagine you're cataloging/annotating/linking a public author/creator of any (digital) work.

  * You know the birth-date.
  * Or the date a group was founded.
  * The usual "Agents" date metadata standards.

Now if I `titleled` the catalog entry Object of the band XBloome with:

>  🌟️$timestamp/$title

And selected the date/year I believe the band was formed.
As fuzzy (00-00 and all) as I like.

**Examples:**

>  =🌟️200610/XBloome  
>  =🌟️2006/XBloome  
>  =🌟️20XX12?/XBloome  
>  =🌟️20061200/XBloome  


```
$timestamp = 20061200
$title = XBloome
$random = <none> (collision friendly :P)
```

Yes, $random is empty.
So it's quite likely that someone else created an Object for the band XBloome using the same ID.
On purpose.

And the examples show some "fuzziness" in the exact date. And also that CFIDs $timestamp may contain fuzzy dates. There are [library cataloging standards for that](https://www.loc.gov/standards/datetime/background.html).

Now if we connect different meta/data collections ID'd like that, or query an online shared-source - matching entries would collide - theferore providing the option to `update` our existing Objects - without requiring that more (address) space.

So our "database" entries become auto-annotated, auto-referenced by default over time.

This is the "collision-friendly" nature of this design.
And one possible benefit of such a syntax.

It would also be very easy to memorize for anyone:

> 2006/XBloome

You could still easily create a related, yet different, separate, non-colliding Object.

`$timestamp_nsec/$title/$longer_random`

So simply choose nanosecond-precision and some more random-random characters.
That address space should be quite sufficient for a while, I guess?
What's the expected context (to collide/exist in) and lifespan of your Objects?

Remark: The nanosecond part of the timestamp may probably be good to have a human-digestable separator before.
Like `20250103T133700-162/XBloome`: The nanoseconds shall /can/ be zero-padded, but may be not for human readability.
Filemanagers and tools may know of this and be able to still sort "by time", knowing the nanoseconds just "count up".

Keep in mind that `2006/XBloome` was also sufficient to get what you wanted: because it's linked to other Objects (if copies exist) that may have "more or different" information about the "XBloome" from 2006.

The data you're querying or working with may of course be "as fuzzy as short-and-uniform their ID is".
Intentionally.

Yet never losing the option to keep certain Objects alive and sharp as new.
By each having their full-ID.


## What if Object IDs collide?

So there's the case when:

  * The $title
  * The $timestamp (nanoseconds = 10^9 digits)
  * The $random sequence (random length, preferred ASCII charset)

...are exactly the same.


Okay.

How do we deal with it?

I suggest this:

  * First of all: Thank the universe for a very interesting coincident. Maybe you 2 should talk to each other?
  * Then select: merge?
  * Or prefer yours/theirs/other?
  * And: this includes relationships/links to other meta/data.
  * Policy rule (=preference) setup option to store and configure that selection.

### The Mismatch-Score

This is simply a value of "diff-intensity" when deciding what actions to take ton colliding Object IDs.

In case the meta/data content(s) differ "too much" (beyond a configurable, sane-default threshold) - the user may optionally be altered and asked for their opinion. So if some things that really refer to something completely different (eg 2 different bands - not even sharing the same metadata "title", etc.).

**Exactly the same we already do with version control conflict handling.**

Or manually if we come across such a (rather rare) case.

Again, I do consider the case of actually colliding Object IDs (given the above syntax) to be very high or practically significant, too: So most of the time there isn't even any problem.


# Serious Collisions

What if: a merge ain't sufficient. We must keep separate copies of Objects?
Who stays, who gets a new ID?

  * flip a coin
  * ask policy/rules/user

Same we do already in such a case.

What's new though is: Use extended attributes to remark (if desired) the "old" ObjectID somehow.
In case a query really needs to make a connection, this `provenance` metadata keeps the chain of information available.
And can accumulate over time (though quite unlikely).

Same applies to filenames and paths:
They have their place as plain strings in xattrs now.
Zero or more.
Since filenames and paths become "yet another metadata" - a data Object can be "saved" simply getting a unique-enough CFID.
And add some user-provided context string.

Most use-cases will simply require selecting "save" - and you're good.
If you don't want to use version control capabilities of the filesystem or tools - you can simply UP the $random, and $timestamp precision, and you have a poor-human's version search-and-recover system. Noisy, but filtered properly it is fine.

I would be interested in knowing your experiences with serious collisions in real life using CFIDs?


## Heavy and thin and "pure" Data Objects

Objects with shorter, less random IDs (=more collision friendly) will accumulate more "encounter" metadata, by merging or adding references to other Objects.

These may always be both equally: meta or data (payload).

Here's a suggestion for categorization:

  * heavy
  * great
  * light
  * thin
  * link

Meaning:

  1. Heavy is the one including the large-bytesize chunks of data payload.
  2. Great ones are with your preferred working format(s) for data and just enough meta.
  3. Light is meta-only, preferred plaintext (non-binary) - may include wholefile syntax clobs. Still "just meta" no real "data" (payload).
  4. Thin is meta-only, below a certain bytesize of selected keys. 
  5. Link is links where possible and reasonable - and hard-copy strings where it makes sense.

Be generous with your meta!
I believe the computing resources will be sufficent. And can be improved if necessary.



## What if I don't remember the whole "ID"?

No problem.

If you remember parts (title most prominently), then maybe a year?
Or a month? day? particular pattern in sub-seconds or random?

Yes, IDs may also include emojis. Again: Full Unicode support.

So, `2006-XBloome` - and you'll get a list of all entries matching fuzzy-match Object IDs.

Objects with short IDs like that are intended to accumulate meta and relate (or carry) the data, too.

**Examples:**

```
20061225/123456789/XBloome/aj1öf3wle3fa7owief  
2006/XBloome  
200612/XBloome  
20061200/XBloome/lskajdfowihf2a  
```


## What if me or someone else got the date wrong?

So be it.

``` 
20050501/XBloome
200800/XBloome
2006/XBloome
``` 

So there'll be clusters of (un)similar `$timestamp` values - but all having the more or less identical `$title`.
And no relevant random-factor.

One can still work with fuzzy-search unfiltered, but grouped list of IDs here.
And if one of those Objects is under your control: You may see that others "disagree" - and you may take the time to figure out "why".

This would solve one "value/record source" issue?
Or pile up key.n alternative values for the same $key?

Depending on the hardware available, this accumulating-option may still be better (and smaller) than what is current de-facto standard.


## "more prominent" Objects usually get (to keep) a long - or even more awesome ID.

Yes, as long as the values stay within the default syntax, anything custom goes:

  * `🌟️TIMESTAMP/title/RANDOM` (=Anything)
  * `🌟️00001225/Superstar` (=Agent)

Also cool:

  * `🌟️01/xbloome/blue_room` (=song #1 called 'blue room')

May all your collisions go well and be fruitful!
Remember: On collisions, your meta/data meets more meta/data - and your collection might be better annotated/related afterwards?

Everyone is in control over their own collection. If one decides for a certain object precision/style it's fine - as long as the syntax is engine-compatible.

I would advise for keeping the ID short and put metadata there only if it really is useful for someone.


# Is this Object Store compatible?

The good thing about current Object Storage systems is, that it doesn't actually matter what kind of ID you give your objects.
As long as you limit it to ASCII and I guess 256 chars or so, you're on the safe side.

CFIDs used for stored Objects can of course co-exist with any other ID schema - in the same pool.
Again, if collisions should happen: There probably is a reason for it - given the nature of its syntax.


## Feature: Aging Object become "fuzzy".

Transformations could be applied to Objects (defined again by policies) to "lose their precision" (=timestamp sub-seconds index) when being copied and being above a certain age "or condition".

Example:

  * **Original (nsec):** `20061225T133755/XBloome/aj1öf3wle3fa7owief`
  * **Random removed:** `20061225/XBloome`
  * **Minutes precision:** `20061225T1337/XBloome`
  * **Year and month:** `200612/XBloome`

You get the idea.

Any implementation is fine, as long as the data owner/user is fine with it (on their systems).

So by reducing the randomness, and length of the ID string in total, the chances of older Objects to "collide" increase over time (and configured aging parameters). Since the IDs will become less precise = shorter again.
The IDs shrink and flatten down.

Actually, using Object Storage queries to decide which Objects shall be processed "over time" - and how - may be interesting to do.

Implementing and supporting `digital data aging` functionality by default is an interesting way to avoid data-congestion - and overwhelming storage consumption - even running long-term.

If collisions become so popular for certain objects, that they payload version collides as well

There are means to refresh Objects to "keep them alive" longer.
Any Objects not used for over a certain period, are simply merged or prefer mine/theirs and be good with it.
They may even be removed at all if garbage collection policies feel free to do so.

Introducting quasi-natural aging to digital data.
It feels like a good new option.


# Timestamp is providing new space for new ages.

Anyone may from now on call their diner "Mom's best!", and the CFIDs used as web-URL-replacement to resolve "their websites": You get a couple of answers.

Possible duplicates, and possible collisions.

However, `1981-Mom's_Best!` is clearly aka `1981-Moms_Best!-AT`, yet easily distinguishable from `1956-Moms_Best!-AT`. So each new generation gets a new namespace automatically.

Anything currently a URL then at least has a digit for a time-indicator.
Funny thing: By adding $CONTEXT and maybe some $RANDOM, the $TIMESTAMP resolution may not be required to be more than seconds, to be **unique-enough** to store each short-message on the planet. permanently.


# Namespace Hoheit?

Who is allowed to publish what Objects in what name?
- "where?" is the next question.

Same as now on the Internet:
If you now search for "youtube" on your favorite search engine: which link(s) do you follow?

So if a ❤️&⭐️ ID should point to a URL: you do the same. You check its origin.

Therefore: Anyone can write anything into /their/ pools or pools they have write access to.
Same as now. Your local ❤️&⭐️ copy and OS-policies define automatically and by your usage, which links to contain.

It may be necessary to implement preconfigured and user-configurable regex-and-beyond matching capabilites to tune-in-and-filter-out the objects and "namespaces" (=patterns) you're interested in.

A bit like tuning analog TV/Radio in a cyber-future, where everyone has their own radio and TV and printing station - all sending out, accessibly by CFIDs.

This can be very noisy.
But so is the Internet.

Imagine you'd "see" all the Internet traffic happening right now!
And much of that is still IPv4.

Any indexing "AHA-agent" (=keeper of CSV files or Redis/KeyDB caches) may provide you with an answer containing metadata to your "query by CFID" request.

You (or your OS presets) decide, which "nameservers" you trust.
And those nameservers take care to manage "public demands" in their best interest.
Which of course can be creative an even malicious. That's life.

We're in this together now, and usually have great fun together.
So please be nice and use this technology to make you and others happy.

It will do you and all of us good.


## The people are the Hoheit now.

CFID resolution starts out literally with a group of friends.
And yourself to begin with.

No need to remove all doors and windows and be in fear of evildoers on your data.
Your local filesystem can already do CFIDs on your local stuff.
And you'll be amazed how much fun it is to "find your stuff" using these mnemonic strings.

It's trivial to propose "related objects", and to provide filtering and query capabilities. Especially, considering that "the index already is a fully blown attribute-cache database" anyways.

So is the filesystem.
And therefore the access permissions and "Hoheit" over naming Objects is the same as for all eg ZFS data pools worldwide.

If I share Objects, I can do so with others easily:
Simply create a HoloTAR, or use the CFID as filename - and put all else in attributes and related objects.


## Huge ID Bytesize

Yes. the average CFID as I intend it, is huge.
Compared to common alpha-numeric or hash used as IDs. They're really small.

However, most of my desktop workstations and notebooks since around 2010 have more RAM than I actually need most of the time. Currently I'm using 2,4 of 32 GB in my office notebook.

And my whole-life-data-NAS-storage has less than 1 GB "filesystem and de-embedded metadata in attributes" stored in a single CSV.

I don't intend to save the few mega-or-gigabytes in ID-glyphs, and I encourage to use ASCII-and-Unicode-Art to make things your own, and put life into them!

By natively supporting UTF-8 and even Emoji glyphs, your namespace becomes virtually as unlimited and inter-connecting as languages can be.

The CFID provides a form of natural pattern-language to store, address and refer to "data" - Objects of Information.

I boldly assume that "hardware is not an issue" these days, given the benefits of CFIDs providing human-natural-interface capabilities.

Of course I remember "⭐️wikipedia❤️"!
Or: certainly, I know where to find "⭐️wikidata❤️"!
and so on.

These will resolve to "beacon Objects" that collide = match with these low-precision "search beacon IDs". Your local configuration decides which beacons and links you follow.

That's it.


# Viruses infecting the namespaces and resolution services.

Of course.
Again, I ask you: Why would anyone do that? Can we sort that out please?
What are you trying to tell us, by disrupting our efforts to have a nice life together on the planet?

Well, if any "malicious" break-in should happen currently to DNS servers, what then?

Same level of OS-security and cache-copy-sync authentication mechanisms are applied as are currently standard for DNS.

The Hoheit lies with the owners/admins of the individual pools.

This is the Internet. We all have equal space an dominions here. If you trust each other.

If a AHA-nameserver should be compromised and handing out malicions beacon-objects or links, this would be bad. However, I presume a signature-style hashing algorithm may suffice (rsync over SSH then SHA?) to detect and drop tampered nameserver replies.

Similar to current DNS.
However that works: it does.

It's not because you have to pay for a domain: Your provider could simply "for fun" put up some unused domains for themselves by writing text into their config files and restarting the daemons. :)

It's all about trust and ability to focus.
Focusing on the "data objects and sources" you trust and you engage with.

Similar to email or messenger contacts.
Start there.

I'm saying, that the anti-evil-measures of the AHA-network are more like in the real world, and it's up to us to make it work nicely.

If people want to mess up all comm-channels for fun-or-profit to a point where it becomes malicious and disruptive: We may want to pay attention for a change?

That's also a reason I chose ❤️&⭐️ as ID-Identifier, to remind me daily what life is all about.
Definitely love, peace and a bit of magic. ;)
Paying attention and having best intentions:
We can have fun and trust with data and digital again:
if we trust each other "in the real world".

So again: You trust your DNS and web-content/service provider(s) - you can also trust that AHA-IDs can securely be resolved and managed. Just like DNS.



# Fix colliding IDs? = Refresh them: Add "fuzz-to-copy"

Although it requires a write-operation to the Object filesystem (problematic for tape, or other offline media), but in all other cases:

if one encounters a colliding CFID, where the hash of the payload (file-contents) is different:
One can simply append $RANDOM to the existing $RANDOM part of the ID.
Literally "add-fuzz-to-copy".

This would still keep the visible ancestry/relationship by ID: this is like `family` of data.
And "remembering" your valued data is keeping it in shape.
Remembering and toggling "a bit or byte(s)".



# Working prototype

I know how to build a working prototype for this right now, and me and my colleague already have working parts of it in action on our local network systems:

All stages and parts consist of FOSS stacks of production-stable implementations and documentation.
With slight alterations to orchestrate the full potential of a graph-DB data storage system.

If interested, please contact me:
aha at ArkThis.com



# Can I use CFIDs as file/foldername?

Indeed! Absolutely!
This ID can absolutely be used as-is described here for filenames.

> **Yes, people can and shall use it too, but:**
> The "title" or other metadata describing this Object go in separate, regular filesystem fields.

**So if you feel like abusing the `title` component like we used to long-label filenames, please do not.** :)

The fact that there's a `$timestamp + $title` part in your ID makes it already pretty fine as it is. No need to overload it to "find your stuff" - or "make sure it's unique".

It's okay.

And anything else you'd like to add:
Put the meta with the data: In the filesystem.

Not in the ID.
Thank you. 😘️



# Examples for fun with CFIDs:

## Good example: Default for coming from "FinF": Files-in-Folders to Object ID thinking.

> $TIMESTAMP=%yyyy%mm%ddT%H%M%S (from creation timestamp in filesystem)
> $CONTEXT=currentFolder/Filename.xxx
> $RANDOM=on demand, as short and visually simple/appealing as possible.

This bridges a gap from FinF (Files-in-Folders) to Object-ID storage designs.
And keeping it "fuzzy-interoperable" thanks to CFIDs with IDs `full-path/filename.xxx` default.

Yet, please be aware:
This is *just* the technical identifier.
The folder is not "a location" anymore. It ascended to "plain metadata". yet-another-key-value-pair. Nothing special, yet very allstar-metadata-key: `user.path` and `user.filename`!

Fun fact: Unicode / UTF-8 and emojis are fully supported and users encouraged to use them "wisely" and in styles that fit their likings. Anything goes.


# Here's ONE catch : "no space allowed in ID"

Literally: CFIDs can be anything. Unicode and all.
BUT: /NO/ space between characters.
;)

please.
Thank you.

Let that thing rest once and for all.
You get the whole free world of filesystem attributes for all metadata you'd loove to put in a file-or-foldername, but no: those days are over.

Let it be good:

Put meta in the key/value attributes (up to 64kB each), and the "largest" stuff currently as payload property: and let it be good.

It has an Identifier value that simply never has issues, because it never - are we clear? :P - please not - has any "space 0x20 dec32 " " - character" in there: no.  - because it never had "a syntax-space" in it.

:)

Enjoy CFID-ing your stuff!


# Reference and proof-of-concept implementation & python library

Program [idaha](https://github.com/pjotrek-b/mercs/blob/main/helpers/idaha.py):

  * auto-generates CFIDs for files/folders.
  * defaults to creation-timestamp in seconds-precision.
  * precision and patterns can be tuned by-part.
  * highly as-is to use: "just works"
  * include `currentfolder/filename.xxx` as $CONTEXT, and even "cover.jpg" is hardly a colliding object collision case anymore.

  * Music example: `⭐️20070129T175516-x_marks_the_spot/cover.jpg❤️`

  * idaha.py includes a ready-to-use cfid-generator and handling class `CFIDGenerator`.


> **Have fun with data!**

