# *bsc-snapshots*


- *[Geth](#geth)*
    - *[Geth fast node](#geth-fast-node)*
    - *[Geth full node](#geth-full-node)*
- *[Erigon](#erigon)*
    - *[Erigon fast node](#erigon-fast-node)*
- *[How to download](#how-to-download)*
    - *[pipeline download and extract](#pipeline-download-and-extract)*
    - *[multithreaded download](#multithreaded-download)*

## Geth
### Geth fast node

| Field |Value |
| --- | --- |
| Version | [v1.4.14](https://github.com/bnb-chain/bsc/releases/tag/v1.4.14) |
| Block | [42447018](https://bscscan.com/block/42447018) (Sep-21-2024 11:56:04 AM +UTC) |
| Link | `https://snapshots.48.club/geth.fast.42447018.tar.zst` |
| Size | 319.91G <-> 352.55G |
| SHA256 | `84be08102c964fbedb7ffd0d2b7d9b5764208d0549f0e4cae50c1c9762a4269c` |
| Flags | `--history.transactions=90000 --syncmode=full --db.engine=pebble --tries-verify-mode=none` |
| Disk Suggestion | Minimum(NVMe ≥ 500G), Suggestion(NVMe ≥ 1T) |

[Back to TOC](#bsc-snapshots)

### Geth full node

| Field |Value |
| --- | --- |
| Version | [v1.4.15](https://github.com/bnb-chain/bsc/releases/tag/v1.4.15) |
| Block | [42451514](https://bscscan.com/block/42451514) (Sep-21-2024 03:41:44 PM +UTC) |
| Link | `https://snapshots.48.club/geth.full.42451514.tar.zst` |
| Size | 872.26G <-> 954.03G |
| SHA256 | `ea23cc8861bb1acc9022463b535441668830e8b9447cdfcdc562cefccad29e52` |
| Flags | `--history.transactions=90000 --syncmode=full --db.engine=pebble` |
| Disk Suggestion | Minimum(NVMe ≥ 1.2T), Suggestion(NVMe ≥ 2T) |

[Back to TOC](#bsc-snapshots)

## Erigon
### Erigon fast node

| Field |Value |
| --- | --- |
| Version | [v1.2.16](https://github.com/node-real/bsc-erigon/releases/tag/v1.2.16) |
| Block | [42332397](https://bscscan.com/block/42332397) (Sep-17-2024 12:12:43 PM +UTC) |
| Chaindata | `https://snapshots.48.club/erigon.42332397.tar.zst` |
| Size | 388.67G <-> 823.70G |
| SHA256 | `12f4fcc4b6871a345678ae22da2268f43cd054694a56fcf675c8460bd6b9780b` |
| Flags | `--prune=htrc --db.pagesize=16k --prune.h.older=5000 --prune.r.older=5000 --prune.t.older=5000 --prune.c.older=5000` |
| Disk Suggestion | Minimum(NVMe ≥ 1T & HDD > 2T), Suggestions(NVMe ≥ 4T) |

### Erigon Snapshot Directory

| Field |Value |
| --- | --- |
| Snapshots | `https://snapshots.48.club/snapshots.42210000.tar.zst` |
| Size | 985.45G <-> 1186.84G |
| SHA256 | `41b6eb22a590a8a558340ebdf55e5e59e46719957b2c0d4b46ca50745d8b41c3` |

[Back to TOC](#bsc-snapshots)

## How to download
### pipeline download and extract

```bash
wget $Link -O - | zstd -cd | tar xf -
```

### multithreaded download

```bash
aria2c -s4 -x4 -k1024M $Link -o $save_path
zstd -cd $save_path | tar xf -
openssl sha256 $save_path # checksum verification, optional
```

[Back to TOC](#bsc-snapshots)
