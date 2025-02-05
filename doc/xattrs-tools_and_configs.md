# Tools

## Samba

Set the config option `ea support = yes` in your `smb.conf`.
Quote from [Official Samba documentation](https://www.samba.org/samba/docs/current/man-html/smb.conf.5.html#idm3356)

```
This boolean parameter controls whether smbd(8) will allow clients to attempt to access extended attributes on a share. In order to enable this parameter on a setup with default VFS modules:

  * Samba must have been built with extended attributes support.
  * The underlying filesystem exposed by the share must support extended
    attributes (e.g. the getfattr(1) / setfattr(1) utilities must work). 

Note that the SMB protocol allows setting attributes whose value is 64K bytes long, and that on NTFS, the maximum storage space for extended attributes per file is 64K. On some filesystem the limits may be lower. Filesystems with too limited EA space may experience unexpected weird effects. The default has changed to yes in Samba release 4.9.0 and above to allow better Windows fileserver compatibility in a default install.

Default: ea support = yes 
```


## TAR

`$ tar --xattrs my_backup.tar /data/with/xattrs/used`

TAR has different options to deal with extended attributes.
Interesting that the only example for excluding xattrs is to *not* include the user namespace.

Quote from `man tar`:

```
Extended file attributes
       --acls Enable POSIX ACLs support.

       --no-acls
              Disable POSIX ACLs support.

       --selinux
              Enable SELinux context support.

       --no-selinux
              Disable SELinux context support.

       --xattrs
              Enable extended attributes support.

       --no-xattrs
              Disable extended attributes support.

       --xattrs-exclude=PATTERN
              Specify the exclude pattern for xattr keys.  PATTERN is a POSIX regular expression, e.g.  --xattrs-exclude='^user.',
              to exclude attributes from the user namespace.

       --xattrs-include=PATTERN
              Specify the include pattern for xattr keys.  PATTERN is a POSIX regular expression.
```


## Rsync

`$ rsync -X ...`

Quote from `man rsync`

```
-X, --xattrs                preserve extended attributes
```



# Fileystems

## ZFS

> Works out of the box.


## EXT4

> Works out of the box.


## Btrfs

> Works out of the box.

I've initialized a test partition with node size 64kB, to test how large data can be stored as xattrs.
