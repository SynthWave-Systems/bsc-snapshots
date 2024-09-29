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
| Block | [42671994](https://bscscan.com/block/42671994) (Sep-29-2024 07:43:02 AM +UTC) |
| Link | `https://snapshots.48.club/geth.fast.42671994.tar.zst` |
| Size | 322.47G <-> 355.73G |
| SHA256 | `52bac31ce84648fb799a6a73522a5682a30bee4b2281b0e9736db6a6b176b2cc` |
| Flags | `--history.transactions=90000 --syncmode=full --db.engine=pebble --tries-verify-mode=none` |
| Disk Suggestion | Minimum(NVMe ≥ 500G), Suggestion(NVMe ≥ 1T) |

[Back to TOC](#bsc-snapshots)

### Geth full node

| Field |Value |
| --- | --- |
| Version | [v1.4.15](https://github.com/bnb-chain/bsc/releases/tag/v1.4.15) |
| Block | [42615347](https://bscscan.com/block/42615347) (Sep-27-2024 08:30:33 AM +UTC) |
| Link | `https://snapshots.48.club/geth.full.42615347.tar.zst` |
| Size | 873.39G <-> 954.28G |
| SHA256 | `b28a23a4184b913e8c4254d1845452fd16caf31e0f7aa0c9533a60d373e21263` |
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
