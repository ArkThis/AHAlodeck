# Notes on tests with btrfs.

First note:
I want an alias for btrfs. I feel a strain-inury in my fingers coming up, when trying to type it too often. I'm already practicing a different finger pattern to type it.

Apart from that, I'm pretty amazed by btrfs so far.

Reading doubts on the web, were well-counterbalanced by the fact that RedHat and Suse seem to use it as root-filesystem by default, since 10 years. I'd say that sounds stable enough.


# Formatting a partition

I'm not yet sure whether to wrap btrfs in lvms, or in paritions - or even paritionless?
Right now I'm doing it "classic": simple linux-filesystem partition (GPT), and mkfs.btrfs on that /dev.

Here's a text-screenshot of mkfs with and without "duplicate metadata" profile selected.
The difference is 8MB (single) to 256MB(dup). Seems "a lot more", but it's still "just a few hundred megs" to be honest.

You can RPi-even-Arduino that quite easily, I presume?

Here's the screenshot:

```
$:~/Downloads/taggedfs-0.3$ sudo mkfs.btrfs -d single -n 4096 -L AHA_Playground /dev/nvme0n1p3 -f
btrfs-progs v5.4.1 
See http://btrfs.wiki.kernel.org for more information.

Detected a SSD, turning off metadata duplication.  Mkfs with -m dup if you want to force metadata duplication.
Label:              AHA_Playground
UUID:               60357cec-d501-4956-831d-614d521e2xxx
Node size:          4096
Sector size:        4096
Filesystem size:    25.00GiB
Block group profiles:
  Data:             single            8.00MiB
  Metadata:         single            8.00MiB
  System:           single            4.00MiB
SSD detected:       yes
Incompat features:  extref, skinny-metadata
Checksum:           crc32c
Number of devices:  1
Devices:
   ID        SIZE  PATH
    1    25.00GiB  /dev/nvme0n1p3

$:~/Downloads/taggedfs-0.3$ sudo mkfs.btrfs -d single -n 4096 -m dup -L AHA_Playground /dev/nvme0n1p3 -f
btrfs-progs v5.4.1 
See http://btrfs.wiki.kernel.org for more information.

Label:              AHA_Playground
UUID:               fad6a9f1-4561-47a7-b002-24a43a5697dd
Node size:          4096
Sector size:        4096
Filesystem size:    25.00GiB
Block group profiles:
  Data:             single            8.00MiB
  Metadata:         DUP             256.00MiB
  System:           DUP               8.00MiB
SSD detected:       yes
Incompat features:  extref, skinny-metadata
Checksum:           crc32c
Number of devices:  1
Devices:
   ID        SIZE  PATH
    1    25.00GiB  /dev/nvme0n1p3
```

See: https://btrfs.readthedocs.io/en/latest/mkfs.btrfs.html#profiles


# Metadata size / limits

See: https://btrfs.readthedocs.io/en/latest/Administration.html#btrfs-specific-mount-options


```
max\_inline=<bytes>

    (default: min(2048, page size) )

    Specify the maximum amount of space, that can be inlined in a metadata b-tree leaf. The value is specified in bytes, optionally with a K suffix (case insensitive). In practice, this value is limited by the filesystem block size (named sectorsize at mkfs time), and memory page size of the system. In case of sectorsize limit, there’s some space unavailable due to b-tree leaf headers. For example, a 4KiB sectorsize, maximum size of inline data is about 3900 bytes.

    Inlining can be completely turned off by specifying 0. This will increase data block slack if file sizes are much smaller than block size but will reduce metadata consumption in return.
```



```
_ratio=<value>

    (default: 0, internal logic)

    Specifies that 1 metadata chunk should be allocated after every value data chunks. Default behaviour depends on internal logic, some percent of unused metadata space is attempted to be maintained but is not always possible if there’s not enough space left for chunk allocation. The option could be useful to override the internal logic in favor of the metadata allocation if the expected workload is supposed to be metadata intense (snapshots, reflinks, xattrs, inlined files).
```


It really feels like going to the jungle (of filesystems and their documentation) of details that seem to exist, but hardly used - but waiting to be rediscovered. Exciting!

