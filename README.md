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
| Block | [42852745](https://bscscan.com/block/42852745) (Sep-29-2024 07:43:02 AM +UTC) |
| Link | `https://snapshots.48.club/geth.fast.42852745.tar.zst` |
| Size | 321.20G <-> 353.88G |
| SHA256 | `189a97e5702b1c48c82d620218f93ac760813ab9673eaf6ee0d6292d5de02433` |
| Flags | `--history.transactions=90000 --syncmode=full --db.engine=pebble --tries-verify-mode=none` |
| Disk Suggestion | Minimum(NVMe ≥ 500G), Suggestion(NVMe ≥ 1T) |

[Back to TOC](#bsc-snapshots)

### Geth full node

| Field |Value |
| --- | --- |
| Version | [v1.4.15](https://github.com/bnb-chain/bsc/releases/tag/v1.4.15) |
| Block | [42679211](https://bscscan.com/block/42679211) (Sep-29-2024 01:43:53 PM +UTC) |
| Link | `https://snapshots.48.club/geth.full.42679211.tar.zst` |
| Size | 875.04G <-> 956.77G |
| SHA256 | `2d984093f67ec741165cc6f76d176be5d28945736e45fd0975c2154a4c4249f7` |
| Flags | `--history.transactions=90000 --syncmode=full --db.engine=pebble` |
| Disk Suggestion | Minimum(NVMe ≥ 1.2T), Suggestion(NVMe ≥ 2T) |

[Back to TOC](#bsc-snapshots)

## Erigon
### Erigon fast node

| Field |Value |
| --- | --- |
| Version | [Erigon3](https://github.com/node-real/bsc-erigon/tree/f10d0fe007494b2948ee9805a2e8727380bdb315) |
| Block | [42677102](https://bscscan.com/block/42677102) (Sep-29-2024 11:58:26 AM +UTC) |
| Chaindata | `https://snapshots.48.club/erigon.42677102.tar.zst` |
| Size | 403.40G <-> 661.40G |
| SHA256 | `c7a7dc91c237d84ed4392dd9165497250a89b3a7fa43e6ad42540f68066de174` |
| Flags | `--prune.mode=minimal --chain=bsc` |
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
