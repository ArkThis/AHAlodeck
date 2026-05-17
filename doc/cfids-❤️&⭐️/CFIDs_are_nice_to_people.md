# CFIDs are nice to people.

> "I need something human"
> (Muse, ~2020)

Looking at thousands and thousands of auto-generated CFIDs, overly long, yet still not longer than:

  1. The last 2 parent-foldernames
  2. The filename
  3. +6 chars: 2 separators, 4 hash-fingerprint

But regardless of length:

In order to "identify" a data-object by CFID, you can assign "a shorter" or even completely different one, you may more easily remember.

And as archivist or working with digital collections:
You'll know what your CFIDs will look like.
They are organic.


## Example

Here's auto-generated IDs for "Jeeves and Wooster" in a personal DVD-to-file archive:

`> gx * | grep cfid`

```
user.cfid.id="⭐️20080717T110202-Jeeves_and_Wooster_(1990)/season_1/Jeeves_And_Wooster_-_1x01_-_Jeeves_Takes_Charge.avi-77bb❤️"

user.cfid.id="⭐️20080717T102736-Jeeves_and_Wooster_(1990)/season_1/Jeeves_And_Wooster_-_1x02_-_Tuppy_And_The_Terrier.avi-8c82❤️"

user.cfid.id="⭐️20080717T112804-Jeeves_and_Wooster_(1990)/season_1/Jeeves_And_Wooster_-_1x03_-_The_Purity_Of_The_Turf.avi-6a9e❤️"

user.cfid.id="⭐️20080717T112952-Jeeves_and_Wooster_(1990)/season_1/Jeeves_And_Wooster_-_1x04_-_The_Hunger_Strike.avi-e125❤️"

user.cfid.id="⭐️20080717T112956-Jeeves_and_Wooster_(1990)/season_1/Jeeves_And_Wooster_-_1x05_-_Brinkley_Manor.avi-7112❤️"
```

Working with them is great:
I only need to remember parts of the signature - and a possible date-range, and I'll very likely have proper matching hits. A short(er) CFID can be assigned additionally.
CFID-implementations always support multi-IDs per Object on purpose.

So you can do this:

### Find a most-likely bit-exact copy of that episode file you have right there (#77bb):

> `⭐️2008-Jeeves_and_Wooster_01_Jeeves_Takes_Charge-77bb❤️`:

This, btw would serve as "unique-enough pattern" for any data, suitable as filename /AND/ ObjectID.
With "collisions" with other copies expected and intended. Allowing to easily pull "exactly the 77bb version" of that recording out of any-sized storage.

You could probably web-search for parts of an CFID to get what you were looking for.

So the "collision-friendliness" of its syntax serves as a natural finding-aid:
You only need to remember "so little" about the actual CFID string.


### More fuzzy searches by ID:

The most-likely /that episode/, recorded off-air around 2008:

> `⭐️2008-Jeeves_and_Wooster_Takes_Charge❤️`


...or simply "any copy from that show produced in 1990", simple to remember.

> `⭐️1990-Jeeves_and_Wooster_Takes_Charge❤️`


... or in simple season/episode syntax:

> `⭐️1990-Jeeves_and_Wooster_1x01❤️`


Or simply strip them down to "admin and catalogers agree" version, like:


```
⭐️2008-Jeeves_and_Wooster_(1990)_1x02_Tuppy_And_The_Terrier.avi-8c82❤️

⭐️2008-Jeeves_and_Wooster_(1990)_1x03_The_Purity_Of_The_Turf.avi-6a9e❤️

⭐️2008-Jeeves_and_Wooster_(1990)_1x04_The_Hunger_Strike.avi-e125❤️

⭐️2008-Jeeves_and_Wooster_(1990)_1x05_Brinkley_Manor.avi-7112❤️
```

As in-place use for filenames.
And I bet they would not collide unwanted. In any folder of any collection worldwide.

That is "unique enough". Based on the fact that "time+context" opens up an incredible space for ID-allocation, which - by length of characters and glyphs = possibly different combinations.


# What's wrong with UUIDs? Why not simply use hashes?

Good point.

> 2a29af7a-46d6-4828-a416-a9d1b80192d3

Of course I like the purpose and idea of hashcodes, but I don't like working with uuids.
(Especially not when dealing remotely without proper bi-directional clipboard support...)

I find uuids impossible to remember and uncomfortable to work with.

CFIDs are nice to look at, and can be used even if one only remembers it "wrong" ;)
That's natural. That's organic.

And that's what I want back in computing:

> Something (for) human(s).


# The 4-char fingerprint mnemonic

The last 4 chars (seemingly random) are derived from a binary hash of the payload data.

`> gx * | grep hash.md5`

```
user.hash.md5="**77**e12ccde87db0ec170981f9a065b3**bb**"
user.hash.md5="**8c**288a83095e8e8673ee808b65abcb**82**"
user.hash.md5="**6a**ac69e98928545d7f7dd83ed700e5**9e**"
user.hash.md5="**e1**da48bc77926706dad0d2d9334500**25**"
user.hash.md5="**71**0d5c584568907609b6544987286c**12**"
```

These turn out to be incredibly nice-to-use mnemonics:

  * 77-bb
  * 8c-82
  * 6a-9e
  * e1-25
  * 71-12

If you can remember any date, or "context string" - and these "random" numbers:
You're quite likely to find what you were looking for.

For an "important" or popular version of an object, you may simply assign emoji glyphs to these "variables":

  * 77-bb = 🌈️
  * 8c-82 = 🌻️
  * 6a-9e = 🐓️
  * e1-25 = 💾️
  * 71-12 = 🍀️

If you can remember any date, or "context string" to find "objects related to that show".
If you remember a fingerprint or the emoji: you can use a possibly very short search-ID to find what you were looking for.


Enjoy the nature of the syntax of this kind of "collision-friendly" identifier.
