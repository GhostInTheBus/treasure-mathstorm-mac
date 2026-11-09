# TIL

* The archive.org item `tmscd-2` is a plain ISO9660 PC disc. It holds `TMS16.EXE` for Windows 3.1 and `TMS32.EXE` (a 32 bit PE, dated 1996) for Windows 95, plus Smacker video and Miles sound libraries and `TMSCD.INI`. There is no Mac HFS partition.
* The Mac build lives on the v2.0 hybrid Win/Mac disc, about 243 MB as an ISO.
* Both archive.org copies of that hybrid (`tmswincd_v2` and `TMSWINCD`) fail in Infinite Mac with an HTTP 500 on one chunk of the image, so the emulator hangs on the read.
* Macintosh Garden serves the same disc as a 128 MB zip and Infinite Mac's built in Garden browser handles it, unzips it and mounts it.
* Passing a zip straight to the `cdrom=` URL parameter does not work. The emulator sees an unreadable disk and offers to initialize it. Cancel that prompt and never initialize.
* Infinite Mac only lets the in emulator downloader fetch from an allow list of sites such as archive.org and Macintosh Garden. That is why the Garden browser is the easy path.
* Under emulation, select the app icon and use File, Open. A fast double click often does not register.
* The game asks for 640x480, which is why the link above sets `screenSize=640x480`.
