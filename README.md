# Calico Miner

[![Build status](https://github.com/calico-project/calico-miner/actions/workflows/ci.yaml/badge.svg)](https://github.com/calico-project/calico-miner/actions/workflows/ci.yaml)
[![GitHub release](https://img.shields.io/github/v/release/calico-project/calico-miner.svg)](https://github.com/calico-project/calico-miner/releases)
[![GitHub license](https://img.shields.io/github/license/calico-project/calico-miner.svg)](https://github.com/calico-project/calico-miner/blob/main/LICENSE-APACHE)
[![GitHub downloads](https://img.shields.io/github/downloads/calico-project/calico-miner/total.svg)](https://github.com/calico-project/calico-miner/releases)
[![Join the Calico Discord Server](https://img.shields.io/discord/1233113243741061240.svg?label=&logo=discord&logoColor=ffffff&color=5865F2)](https://discord.com/invite/XXXXXX)

A Rust binary for mining Calico with the [AstroX](https://github.com/calico-project/AstroX)
algorithm.

## Installation

### Install from Binaries

Pre-compiled binaries for Linux `x86_64`, Windows `x64` and macOS `x64`
and `aarch64` can be downloaded from the [GitHub release](https://github.com/calico-project/calico-miner/releases)
page.

### Build from Source

To compile from source you need to have a working Rust and Cargo
installation, run the following commands to build `calico-miner`:

```
git clone https://github.com/calico-project/calico-miner
cd calico-miner
cargo build --release
```

## Usage

To start mining you need to run a [Calico full node](https://github.com/calico-project/rusty-calico). 
You also need to have an address to send the mining
rewards to. Running `calico-miner -h` will show all available command
line options:

```
A Calico high performance CPU miner

Usage: calico-miner [OPTIONS] --mining-address <MINING_ADDRESS>

Options:
  -a, --mining-address <MINING_ADDRESS>
          The Calico address for the miner reward
  -s, --calicod-address <CALICOD_ADDRESS>
          The IP of the calicod instance [default: 127.0.0.1]
  -p, --port <PORT>
          calicod port [default: Mainnet = 22110, Testnet = 22210]
  -d, --debug
          Enable debug logging level
      --testnet
          Use testnet instead of mainnet [default: false]
  -t, --threads <NUM_THREADS>
          Amount of miner threads to launch [default: number of logical cpus]
      --devfund <DEVFUND_ADDRESS>
          Mine a percentage of the blocks to the Calico devfund [default: Off]
      --devfund-percent <DEVFUND_PERCENT>
          The percentage of blocks to send to the devfund [default: 1]
      --mine-when-not-synced
          Mine even when calicod says it is not synced, only useful when passing `--allow-submit-block-when-not-synced` to calicod  [default: false]
      --throttle <THROTTLE>
          Throttle (milliseconds) between each pow hash generation (used for development testing)
      --altlogs
          Output logs in alternative format (same as calicod)
  -h, --help
          Print help
  -V, --version
          Print version
```

To start mining you just need to run the following:

```
./calico-miner --mining-address calico:XXXXX
```

This will run the miner on all the available CPU cores.

## Hive OS and mmpOS

You can always download the most recent HiveOS flight sheet and mmpOS miner profile from our website.

- [HiveOS Flight Sheet](https://calicocoin.org/downloads/hive-os/)
- [mmpOS Miner Profile](https://calicocoin.org/downloads/mmp-os/)

## Development Fund

**NOTE: This feature is off by default**

The devfund is a fund managed by the Calico community in order to
fund Calico development.

A miner that wants to mine a percentage into the dev-fund can pass the
following flags:

```
./calico-miner --mining-address=<calico:XXXXX> --devfund=calico:qrxf48dgrdkjxllxczek3uweuldtan9nanzjsavk0ak9ynwn0zsayjjh7upez
```

Without specifying `--devfund-percent` it will default to 1%. If you
want to change the percentage, you can pass the option
`--devfund-percent=XX.YY` to mine only XX.YY% of the blocks into the
devfund.

## License

Calico miner is dual-licensed under the [MIT](https://github.com/calico-project/calico-miner/blob/main/LICENSE-MIT)
and [Apache 2.0](https://github.com/calico-project/calico-miner/blob/main/LICENSE-APACHE)
license.
