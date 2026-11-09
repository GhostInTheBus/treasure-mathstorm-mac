# Self hosting Infinite Mac with a disc preloaded

This is the recipe for running your own copy of [Infinite Mac](https://github.com/mihaip/infinite-mac) on a home server, behind a password, with one disc already mounted. It removes the 3 minute disc download every session. No game data lives in this repo. You supply your own disc image.

## Overview

* Infinite Mac is a browser emulator built to run on Cloudflare Workers plus R2 storage.
* You can run the same worker locally with `wrangler dev` (workerd under the hood). No Cloudflare account is needed for that part.
* The worker expects an R2 bucket for disc and disk chunks. A self hosted copy swaps that for local files.
* A tiny Node front server adds a password, `noindex` headers, range requests for the disc file and an optional download page.

## Steps

1. Clone Infinite Mac and follow its README to build it (`npm install`, then the build scripts).
2. Put your disc image in `CD-ROMs/<category>/<name>.json` as `{"src_file": "<file>.zip", "self_hosted": true}` and rerun the CD library build. This produces `CD-ROMs/build/media/<sha256>.media`.
3. In `worker/cd-rom.ts` and `worker/disk.ts`, the code paths guarded by `import.meta.env.DEV` read from local files. Force them on for your build so the worker serves chunks from disk instead of R2.
4. Keep large chunks outside the wrangler assets directory. Wrangler rejects any asset over 25 MiB, so serve media and disk chunks from your front server instead.
5. Run `wrangler dev -c build/infinite_mac/wrangler.json --ip 127.0.0.1 --port 3128`.
6. Put a Node server in front that:
   * requires HTTP basic auth (compare hashes, never store the plain password in the repo),
   * sends `X-Robots-Tag: noindex, nofollow` and serves a `robots.txt` that disallows everything,
   * serves the disc and disk chunks with `Range` support,
   * proxies everything else to the worker.
7. Launch with the `cdrom=` URL parameter pointing at your library disc so it mounts on boot.

## Keeping it private

* Use a long random subdomain and keep it out of any public page.
* Keep the password in an env file with `chmod 600`.
* A tunnel (for example Cloudflare Tunnel) avoids opening router ports.
* This is a personal setup for a copy you own. Do not share it publicly.

## Gotchas learned the hard way

* Copying files from macOS with `tar` adds `._*` metadata files. Delete them before starting the worker, or it fails with `Invalid or unexpected token`.
* On Synology DSM, a normal user may not have Docker access, and `npm` may live inside the Node.js package folder rather than on the PATH.
* If a port is "taken" and answers with `405`, another service owns it. Pick a different port.
