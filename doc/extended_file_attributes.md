# Extended (File) Attributes (EAs)

Also known as:

  * GNU/Linux: [xattrs](https://en.wikipedia.org/wiki/Extended_file_attributes)
  * MacOS: xattrs or [Resource Fork](https://en.wikipedia.org/wiki/Resource_fork)
  * Windows: [Named Streams](https://learn.microsoft.com/en-us/windows/win32/fileio/file-streams) 

Quote from [DublinCore Paper Article: Universal File System Extended Attributes Namespace (by Francois Revol, 2011)](https://dcpapers.dublincore.org/article/952135759):

> "File-system extended attributes, often abbreviated xattrs, or EAs, are a form of file metadata storage consisting of name-value pairs, and are used in many operating systems, under many forms and names (Resource Fork, Named Streams), for many purposes, either for security concerns (Access Control Lists, Proof Carrying ), fallback for missing file-system properties (DOS attributes, POSIX “atime”) or user-level applications (Leung et al., 2008), from early adopters like the BeOS, up to recent semantic desktops (Möller et al., 2007)."

> "At the file-system level they are usually handled as named raw data attached to the file's structure (inode), without any further semantic attached. Operating Systems then use them for their own purposes, like security, but most of them are left for application use as binary data without any interpretation by the Operating System, just as is done for file content itself."


## Summary

EAs allow to assign key/value data pairs to a filesystem object, like conventional files or folders.
Their tech-designs were envisioned before 2000, and are well-supported in basic components of any major operating system, since around 2005.

Using EAs allows to add metadata to annotate the actual file/folder objects on a data storage - without the need for additional database or spreadsheet applications for most needs. Using 0-Byte file objects, one can even create stand-in replacements for basic database functionalities like describing object relationships.


EAs may play a crucial role in the adoption of reliable annotation on the filesystem level.

