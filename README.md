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
| Block | [43664651](https://bscscan.com/block/43664651) (Nov-02-2024 06:58:48 PM +UTC) |
| Link | `https://snapshots.48.club/geth.fast.43664651.tar.zst` |
| Size | 324.72G <-> 358.06G |
| SHA256 | `304cdefc297c6ebc0f9f59873533f0e04dcfc3986873b3372f0521a1c325d218` |
| Flags | `--history.transactions=90000 --syncmode=full --db.engine=pebble --tries-verify-mode=none` |
| Disk Suggestion | Minimum(NVMe ≥ 500G), Suggestion(NVMe ≥ 1T) |

[Back to TOC](#bsc-snapshots)

### Geth full node

| Field |Value |
| --- | --- |
| Version | [v1.4.15](https://github.com/bnb-chain/bsc/releases/tag/v1.4.15) |
| Block | [43695715](https://bscscan.com/block/43695715) (Nov-03-2024 08:52:17 PM +UTC) |
| Link | `https://snapshots.48.club/geth.full.43695715.tar.zst` |
| Size | 883.02G <-> 965.03G |
| SHA256 | `a52f2e3633b35f3be0aee6aab1396e37810032296d063d825b597bcfc54de954` |
| Flags | `--history.transactions=90000 --syncmode=full --db.engine=pebble` |
| Disk Suggestion | Minimum(NVMe ≥ 1.2T), Suggestion(NVMe ≥ 2T) |

[Back to TOC](#bsc-snapshots)

## Erigon
### Erigon fast node

| Field |Value |
| --- | --- |
| Version | [v1.3.0-alpha5](https://github.com/node-real/bsc-erigon/releases/tag/v1.3.0-alpha5) |
| Block | [43851580](https://bscscan.com/block/43851580) (Nov-09-2024 06:57:26 AM +UTC) |
| Chaindata | `https://snapshots.48.club/erigon.43851580.tar.zst` |
| Size | 328.96G <-> 522.69G |
| SHA256 | `91b6053ba06e607e0c50220426adee7efc44f63abeb39fbb6c29c3acdc92a9f7` |
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
