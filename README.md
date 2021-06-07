![lisp logo](lisplogo.png)

# UUID

UUID is a Common Lisp librabry for generation of universally unique identifiers as described by RFC 4122.

## Description

UUID provides methods for the generation of uuids version 1 (time based), 3 (name based with MD5 hashing), 5 (name based with SHA1 hashing) and 4 (random uuids).

## Platforms

UUID has been run on Clisp (Windows), CMUCL(19d), SBCL(1.0.5 - Linux) and Allegro (Linux). Plattform specific code is needed only for the generation of time based (version 1) uuids for getting the MAC address of an ethernet device. If run in an unsupported lisp implementation a random number will be used for the node id instead of the MAC address.

## History

26 May 2009 - Added suport for Allegron on Linux (Contributed by Andrew Philpot). Added suport for formatting as URN (Thanks to Kim Minh Kaplan).

27 July 2008 - Resolve loading issue due to Ironclad shadowing cl:null. (Reported by Maciek Pasternacki)

20 January 2008 - Fixed uuid-to-byte-array and provided byte-array-to-uuid.

02 October 2007 - Don't print a newline as part of the uuid.

07 July 2007 - Reinitialize *random-state* when loading in SBCL to ensure randomnes of v4 uuids. (Reported by Brian Seitz)

30 May 2007 - Added support for SBCL.

17 April 2007 - Updated the package with the correct file. (Reported by Rafael Cavallaro)

16 April 2007 - Released


## License

[Lisp Lesser GNU Public License (LLGPL)](http://opensource.franz.com/preamble.html)

## Author

Boian Tzonev <boiantz@gmail.com>

## Download

[http://www.dardoria.net/software/uuid.tar.gz](uuid.tar.gz)

## Installation

UUID can be loaded with asdf. After unpacking the archive UUID can be loaded with:

CL-USER> (asdf:oos 'asdf:load-op 'uuid)

## Usage

    CL-USER> (in-package :uuid)

Generation of version 1 (time based) uuid:

    UUID> (make-v1-uuid)
    D79FC180-ED1C-11DB-90E2-345C6EAC45A5

Generation of version 3 (name based MD5) uuid in the DNS namespace:

    UUID> (make-v3-uuid +namespace-dns+ "www.widgets.com")
    3D813CBB-47FB-32BA-91DF-831E1593AC29

Generation of version 4 (random) uuid:

    UUID> (make-v4-uuid)
    5EB052B1-BEF9-40E5-9EC5-D735A12DBF48

Generation of version 5 (name based SHA1) uuid in the DNS namespace:

    UUID> (make-v5-uuid +namespace-dns+ "www.widgets.com")
    21F7F8DE-8051-5B89-8680-0195EF798B6A

## Documentation

***ticks-per-count*** _variable_

Holds the amount of ticks per count. The ticks per count determine the number of possible version 1 uuids created for one time interval. Common Lisp provides INTERNAL-TIME-UINITS-PER-SECOND which gives the ticks per count for the current system so *ticks-per-count* can be set to INTERNAL-TIME-UINITS-PER-SECOND

**+namespace-dns+** _constant_

The DNS Namespace. Can be used for the generation of uuids version 3 and 5.

**+namespace-url+** _constant_

The URL Namespace. Can be used for the generation of uuids version 3 and 5.

**+namespace-oid+** _constant_

The OID Namespace. Can be used for the generation of uuids version 3 and 5.

**+namespace-x500+** _constant_

The x500+ Namespace. Can be used for the generation of uuids version 3 and 5.

**uuid** _class_

Represents an uuid

**(make-uuid-from-string uuid-string)** _function_

Creates an uuid from the string represenation of an uuid. (example input string 6ba7b810-9dad-11d1-80b4-00c04fd430c8)

**(make-null-uuid)** _function_

Returns a NULL uuid (i.e 00000000-0000-0000-0000-000000000000)

**(make-v1-uuid)** _function_

Returns a version 1 (time-based) uuid.

**(make-v3-uuid namespace name)** _function_

Returns a version 3 (named based MD5) uuid.

**(make-v4-uuid)** _function_

Returns a version 4 (random) uuid.

**(make-v5-uuid namespace name)** _function_

Returns a version 5 (name based SHA1) uuid.

**(uuid-to-byte-array uuid)** _function_

Converts an uuid to byte-array.

**(byte-array-to-uuid byte-array)** _function_

Converts a byte-array generated with uuid-to-byte-array to an uuid.

**(print-bytes stream uuid)** _function_

Prints the raw bytes in hex form. (example output 6ba7b8109dad11d180b400c04fd430c8).

**(format-as-urn stream uuid)** _function_

Formats the UUID as URN (example output urn:uuid:ea0e0cb8-7ed8-4b10-8214-1a175e982cc6).

[![emacs logo](emacs.jpeg)](http://www.gnu.org/software/emacs/)
[![opensource](opensource-55x48.png)](http://opensource.org/)
