This directory contains the files needed to build PWB/UNIX 1.0 from
tape.  It requires that you have "expect" and simh's "pdp11"
installed in your path.  To build a new system run:

```sh
   $ ./setup
```

Once you have installed, run it with simh's pdp11 emulator:

```
   $ pdp11 run.conf
   #00=unix
   login: root
   message-of-the-day: PWB/UNIX
   # sync ; sync ; sync
   ^E
   quit
```

Tapes built from

```
tuhs/Distributions/USDL/bostic_pwb.tar.gz
pwb/pwb.2/tape1/
pwb/pwb.2/tape2/
pwb/pwb.2/tape3/
pwb/pwb.2/ecc/

tuhs/Distributions/USDL/spencer_pwb.tar.gz
type/
```

with mksimtape from
https://github.com/open-simh/simtools

```
	tape1: root
mksimtape file1:512 file2:5120 file3:512 file4:512 > pwb_root.tap
	tape2: /usr
mksimtape file1:512 > pwb_usr.tap
	tape3: /sys
mksimtape file1:512 > pwb_sys.tap
	ecc: pwb ecc update
mksimtape file1:512 > pwb_ecc.tap
	type
find eqn croff | bsdcpio -o6 > pwb_type.cpio
mksimtape pwb_type.cpio:512 > pwb_type.tap
```

scripts derive from Tim Newsham's
https://github.com/timnewsham/myv6/

scripts based in part on Angelo Papenhoff's notes
on installing System III
http://squoze.net/UNIX/sysIII_pdp11/Installation

scans of documentation for PWB/UNIX 1.0 can be found at
https://bitsavers.org/pdf/att/unix/PWB_UNIX/

Files in doc directory recreated from sources in the tapes.
