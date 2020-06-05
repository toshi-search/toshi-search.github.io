---
layout: default
---
# **State**
Currently Toshi is an experimental full text search engine written in Rust and based on top of [Tantivy](https://github.com/tantivy-search/tantivy).
Toshi is in a fluxy state right now so it's not recommended to use in production. (unless you are brave) Despite this, being built on top of the Rust programming language
gives Toshi native speed and memory safety that is not found in other full text search engines. (Not to mention not having to deal with GC.)

# **Example**
```bash
curl -X POST http://localhost:8080/rap \
    -H 'Content-Type: application/json' \
    -d '{"query": {"term": {"artist": "beatles"} }, "limit": 1}'
```

```json
{
    "hits": 1,
    "docs": [
        {
            "score": 8.398765,
            "doc": {
                "artist": [
                    "beatles"
                ],
                "genre": [
                    "Rock"
                ],
                "index": [
                    149652
                ],
                "lyrics": [
                    "..."    
                ],
                "song": [
                    "i-should-have-known-better"
                ],
                "year": [
                    2014
                ]
            }
        }
    ]
}
```

# **Building**
```bash
git clone https://github.com/toshi-search/toshi.git
cargo build --release
./target/release/toshi --help

Toshi Search 0.1.1
Stephen Carman <shcarman@gmail.com>
A full text search engine based on Tantivy

USAGE:
    toshi.exe [FLAGS] [OPTIONS]

FLAGS:
    -e, --enable-clustering
    -x, --experimental
        --help                 Prints help information
    -m, --master
    -V, --version              Prints version information

OPTIONS:
    -N, --cluster-name <cluster-name>     [default: kitsune]
    -c, --config <config>                 [default: config/config.toml]
    -C, --consul-addr <consul-addr>       [default: 127.0.0.1:8500]
    -h, --host <host>                     [default: 0.0.0.0]
    -l, --level <level>                   [default: info]
    -n, --nodes <nodes>...                [default: ]
    -d, --data-path <path>                [default: data/]
    -p, --port <port>                     [default: 8080]
```
