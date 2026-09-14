# orbitflare-polygon-proto

Internal crate for [`orbitflare-evm-sdk`](https://crates.io/crates/orbitflare-evm-sdk). Contains the compiled protobuf types for OrbitFlare's Polygon (Bor) gRPC service.

You should not depend on this crate directly. Use [`orbitflare-evm-sdk`](https://crates.io/crates/orbitflare-evm-sdk) instead:

```bash
cargo add orbitflare-evm-sdk --features grpc
```

## Protocol definitions

| Proto | Package | Service | Purpose |
| --- | --- | --- | --- |
| [`bor.proto`](protos/bor.proto) | `bor` | `BorApi` | Polygon Bor gRPC interface - headers, blocks, transaction and Bor block receipts, batch block info, total difficulty, root hash, author, vote-on-hash, and Heimdall span lookups. |
| [`common/common.proto`](protos/common/common.proto) | `common` | - | Shared `H128` / `H160` / `H256` hash types, vendored from [0xPolygon/polyproto](https://github.com/0xPolygon/polyproto). Imported by `bor.proto`; not a service of its own. |

Bindings are generated at compile time by `build.rs` via `tonic-prost-build`; nothing generated is committed, so a `protoc` binary must be available when building.
