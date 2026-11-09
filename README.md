# treasure-mathstorm-mac

Play Super Solvers: Treasure MathStorm (The Learning Company, 1996) in a web browser on any modern computer, using the Mac version of the disc and the open source Infinite Mac emulator.

This repo is just notes and a recipe. It is not a fork. Infinite Mac does all the real work. It contains no game data and never will.

## What you need

1. A desktop browser (Chrome tested).
2. About 4 minutes and a decent connection. The disc image is roughly 130 MB zipped.
3. Your own legal copy of the game. The disc is still under copyright. The steps below fetch a disc image from [Macintosh Garden](https://macintoshgarden.org), a preservation library, so check that is fine where you live.

## Play now

1. Open this link, which starts a Quadra 650 running Mac OS 8.1 at 640x480:

```
https://infinitemac.org/run?machine=Quadra+650&disk=Mac+OS+8.1&ram=64M&screenSize=640x480
```

2. Click the **Macintosh Garden** button at the bottom of the emulator.
3. Type `mathstorm` in the filter box and open **Treasure MathStorm! CD (v2.03)**.
4. Click the `TMSWINCD.iso_.zip` download link and wait. It takes about 3 minutes. The disc then mounts on the emulated desktop and its window opens.
5. Click the **Treasure MathStorm!** app icon once, then choose File, Open. Double clicking is flaky in the emulator.
6. Click **Register Later**. The intro plays and you land on the mountain.

## Why not just use the archive.org item

The archive.org item `tmscd-2` is a PC only disc. It has the Windows 3.1 and Windows 95 builds but no Mac half. The two archive.org copies of the hybrid disc (`tmswincd_v2` and `TMSWINCD`) fail inside Infinite Mac with an HTTP 500 partway through the image. The Macintosh Garden copy loads fine. Details in [docs/TIL.md](docs/TIL.md).

## Known gaps

* There is no one click link. The disc has to be pulled in from Macintosh Garden each session. Self hosting would fix that, see [docs/self-hosting.md](docs/self-hosting.md).
* Only tested in Chrome on one machine. Reports welcome, see [CONTRIBUTING.md](CONTRIBUTING.md).
* The Windows build on the disc has not been verified under Wine.

## Docs

* [docs/TIL.md](docs/TIL.md) what I learned getting this running
* [docs/ELI5.md](docs/ELI5.md) the whole thing explained simply
* [docs/self-hosting.md](docs/self-hosting.md) running your own copy behind a password

## Credits and legal

* [Infinite Mac](https://github.com/mihaip/infinite-mac) by Mihai Parparita, Apache 2.0.
* [Macintosh Garden](https://macintoshgarden.org) for keeping the disc image available.
* Super Solvers and Treasure MathStorm are trademarks of their owners. This project is not affiliated with or endorsed by them.
* Text in this repo is MIT licensed, see [LICENSE](LICENSE).
