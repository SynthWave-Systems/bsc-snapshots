# *bsc-snapshots*


- *[Geth](#geth)*
    - *[Geth fast node](#geth-fast-node)*
    - *[Geth full node](#geth-full-node)*
- *[Erigon](#erigon)*
    - *[Erigon fast node](#erigon-fast-node)*
    - *[Erigon archive node](#erigon-archive-node)*
- *[How to download](#how-to-download)*
    - *[pipeline download and extract](#pipeline-download-and-extract)*
    - *[multithreaded download](#multithreaded-download)*

## Geth
### Geth fast node

| Field |Value |
| --- | --- |
| Version | [v1.4.15](https://github.com/bnb-chain/bsc/releases/tag/v1.4.15) |
| Block | [44139092](https://bscscan.com/block/44139092) (Nov-19-2024 06:33:40 AM +UTC) |
| Link | `https://snapshots.48.club/geth.fast.44139092.tar.zst` |
| Size | 327.66G <-> 361.29G |
| SHA256 | `d4542f98f87c1b2b85dd9a4020e228e7eae880112a9497347078d07807d18d9a` |
| Flags | `--history.transactions=90000 --syncmode=full --db.engine=pebble --tries-verify-mode=none` |
| Disk Suggestion | Minimum(NVMe ≥ 500G), Suggestion(NVMe ≥ 1T) |

[Back to TOC](#bsc-snapshots)

### Geth full node

| Field |Value |
| --- | --- |
| Version | [v1.4.15](https://github.com/bnb-chain/bsc/releases/tag/v1.4.15) |
| Block | [44161287](https://bscscan.com/block/44161287) (Nov-20-2024 01:03:25 AM +UTC) |
| Link | `https://snapshots.48.club/geth.full.44161287.tar.zst` |
| Size | 890.41G <-> UnKnown |
| SHA256 | `249fca7ebbbfb7b16645bd5f3f47e626829d138bedb434f07473ef08380a2430` |
| Flags | `--history.transactions=90000 --syncmode=full --db.engine=pebble --tries-verify-mode=local` |
| Disk Suggestion | Minimum(NVMe ≥ 1.2T), Suggestion(NVMe ≥ 2T) |

[Back to TOC](#bsc-snapshots)

## Erigon
### Erigon fast node

| Field |Value |
| --- | --- |
| Version | [v1.3.0-alpha5](https://github.com/node-real/bsc-erigon/releases/tag/v1.3.0-alpha5) |
| Block | [44093268](https://bscscan.com/block/44093268) (Nov-17-2024 04:22:28 PM +UTC) |
| Chaindata | `https://snapshots.48.club/erigon.44093268.tar.zst` |
| Size | 346.31G <-> 545.46G |
| SHA256 | `798303e8a9a760bb82ef920ee706ab3dc7725ed35c44008396db83f439c979d3` |
| Flags | `--prune.mode=archive --prune.distance.blocks=90000 --prune.distance=90000 --chain=bsc` |
| Disk Suggestion | Minimum(NVMe ≥ 1T), Suggestions(NVMe ≥ 2T) |

[Back to TOC](#bsc-snapshots)

### Erigon archive node

Multi-threaded download via aria2, nothing more

```bash
# install dependencies
sudo apt-get install -y aria2 curl jq
# download snapshot
curl -skL https://raw.githubusercontent.com/48Club/bsc-snapshots/refs/heads/main/script/erigon_archive_download.sh | bash
mv snapshots /data/erigon
# start erigon
erigon3 --prune.mode=archive --chain=bsc --datadir=/data/erigon ...
```

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
