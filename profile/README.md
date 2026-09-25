# AdHoc protocol

Multi-language binary protocol code generator. Describe your protocol once in C# as a DSL, get working
serialization, network plumbing and state machines in Java, C#, TypeScript, C++, Go and Rust.

- **[AdHoc-protocol](https://github.com/AdHoc-Protocol/AdHoc-protocol)** — the protocol description format, the
  agent, the documentation.
- Generators: **[InJAVA](https://github.com/AdHoc-Protocol/InJAVA)** ·
  **[InCS](https://github.com/AdHoc-Protocol/InCS)** · **[InTS](https://github.com/AdHoc-Protocol/InTS)**

## Open source

Beyond the generator, the organization keeps in the open what has been built with it: converters that bring other
schema languages into AdHoc, and whole protocols re-expressed in AdHoc, generated, and bound to the real software
on at least one side. Each repository is self-contained: fetch, build, generate, validate, run.

### Converters to AdHoc protocol

Already have a protocol described somewhere else? Run it through the matching converter and see it as an AdHoc
description: packs, enums, hosts, connections, RPC. The output is a **starting point you refine by hand**, not a
finished protocol — AdHoc says more than any of these formats can — but it is idiomatic AdHoc from the first run,
not a transliteration.

| Converter | Source format | What it comes from |
|:--|:--|:--|
| [ROS2-to-AdHoc](https://github.com/AdHoc-Protocol/ROS2-to-AdHoc) | ROS 2 `.msg` / `.srv` / `.action` | robotics interfaces |
| [DBC-to-AdHoc](https://github.com/AdHoc-Protocol/DBC-to-AdHoc) | Vector CAN database `.dbc` | automotive CAN buses |
| [Avro-to-AdHoc](https://github.com/AdHoc-Protocol/Avro-to-AdHoc) | Apache Avro `.avsc` / `.avpr` | data pipelines, Kafka |
| [Thrift-to-AdHoc](https://github.com/AdHoc-Protocol/Thrift-to-AdHoc) | Apache Thrift IDL | services, Hadoop stack |
| [FlatBuffers-to-AdHoc](https://github.com/AdHoc-Protocol/FlatBuffers-to-AdHoc) | FlatBuffers `.fbs` | games, Apache Arrow |
| [Matter-to-AdHoc](https://github.com/AdHoc-Protocol/Matter-to-AdHoc) | Matter (CSA) cluster XML | smart home devices |
| [ASN1-to-AdHoc](https://github.com/AdHoc-Protocol/ASN1-to-AdHoc) | ASN.1 modules `.asn` | telecom, PKI, X.500 |
| [FIX-to-AdHoc](https://github.com/AdHoc-Protocol/FIX-to-AdHoc) | FIX SBE and QuickFIX dictionaries | electronic trading |
| [MAVLink-to-AdHoc](https://github.com/AdHoc-Protocol/MAVLink-to-AdHoc) | MAVLink dialect XML | drones, flight stacks |
| [DSDL-to-AdHoc](https://github.com/AdHoc-Protocol/DSDL-to-AdHoc) | OpenCyphal / DroneCAN DSDL | vehicle buses |
| [CRSF-MSP-to-AdHoc](https://github.com/AdHoc-Protocol/CRSF-MSP-to-AdHoc) | CRSF and MSP firmware headers | RC links, flight controllers |
| [LwM2M-to-AdHoc](https://github.com/AdHoc-Protocol/LwM2M-to-AdHoc) | OMA LwM2M object XML | IoT device management |

Every converter above is listed under the [`adhoc-converter`](https://github.com/topics/adhoc-converter) topic.

**Two more converters need no repository — they are built into AdHocAgent itself**, so the file you already have
is the only argument:

| Source format | Run | Notes |
|:--|:--|:--|
| [Protocol Buffers](https://protobuf.dev/) `.proto` | `AdHocAgent.exe MyProtocol.proto` | A whole directory works too; extra arguments are import search paths, and a final argument that is not a `.proto` is the output directory. |
| [OpenAPI / Swagger](https://www.openapis.org/) `.json` / `.yaml` | `AdHocAgent.exe api.yaml` | A second argument names the output `.cs`; by default it lands next to the input. |

Same promise as the repositories above: the result is a starting point you refine, not a finished protocol.

### Protocols over AdHoc

A well-known protocol written as an AdHoc description, generated into the hosts it needs, and bound to the real
thing, so the description is checked against live traffic and not only against its spec. These are the reference
for how a serious protocol looks in AdHoc: value packs, conduits, RPC actors, state chains, headers, injected
fields, all in use.

| Repository | Protocol | What is in it |
|:--|:--|:--|
| [CQL-over-AdHoc](https://github.com/AdHoc-Protocol/CQL-over-AdHoc) | Apache Cassandra native protocol, CQL binary protocol v5 | The whole `native_protocol_v5.spec` as one description, the spec's text carried in the doc comments. The generated Java Client and Server hosts. A binding that serves the protocol inside an Apache Cassandra 5.0 node beside the native transport: every request runs through Cassandra's own `execute`, every result is served as a view over the `ResultSet`, no copies, back pressure through the Stream conduits. A Docker node runner, a smoke client, and the same scenario on the native port for comparison. Jars on the releases page. |
