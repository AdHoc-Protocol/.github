# AdHoc protocol

Multi-language binary protocol code generator. Describe your protocol once in C# as a DSL, get working
serialization, network plumbing and state machines in Java, C#, TypeScript, C++, Go and Rust.

- **[AdHoc-protocol](https://github.com/AdHoc-Protocol/AdHoc-protocol)** — the protocol description format, the
  agent, the documentation.
- Generators: **[InJAVA](https://github.com/AdHoc-Protocol/InJAVA)** ·
  **[InCS](https://github.com/AdHoc-Protocol/InCS)** · **[InTS](https://github.com/AdHoc-Protocol/InTS)**

## Converters to AdHoc protocol

Already have a protocol described somewhere else? Run it through the matching converter and see it as an AdHoc
description: packs, enums, hosts, connections, RPC. The output is a **starting point you refine by hand**, not a
finished protocol — AdHoc says more than any of these formats can — but it is idiomatic AdHoc from the first run,
not a transliteration. Each repository is self-contained: fetch the samples, build, generate, validate.

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
