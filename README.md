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
| Version | [v1.4.16](https://github.com/bnb-chain/bsc/releases/tag/v1.4.16) |
| Block | [45012199](https://bscscan.com/block/45012199) (Dec-19-2024 02:13:42 PM +UTC) |
| Link | `https://snapshots.48.club/geth.fast.45012199.tar.zst` |
| Size | 324.26G <-> 348.46G |
| SHA256 | `0a2cccf8735c4a73ae2043f15964c26b0c4b43c417141f60f4910f1a45f1c89a` |
| Flags | `--history.transactions=90000 --syncmode=full --db.engine=pebble --tries-verify-mode=none` |
| Disk Suggestion | Minimum(NVMe ≥ 500G), Suggestion(NVMe ≥ 1T) |

[Back to TOC](#bsc-snapshots)

### Geth full node

| Field |Value |
| --- | --- |
| Version | [v1.4.16](https://github.com/bnb-chain/bsc/releases/tag/v1.4.16) |
| Block | [45003222](https://bscscan.com/block/45003222) (Dec-19-2024 06:44:48 AM +UTC) |
| Link | `https://snapshots.48.club/geth.full.45003222.tar.zst` |
| Size | 823.79G <-> 881.85G |
| SHA256 | `84345fa227c1a666dfc904aa907a836d0d1fee47abb27b499b134426b7ba1fee` |
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
