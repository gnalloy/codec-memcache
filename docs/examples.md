# Examples

[简体中文](examples.zh-CN.md) | [Docs Index](README.md)

## Example 1: Add the Module to an Application

```bash
mkdir gnalloy-app && cd gnalloy-app
go mod init example.com/gnalloy-app
go get gnalloy.org/codec-memcache@dev
go doc gnalloy.org/codec-memcache
```

## Example 2: Inspect Current Packages

The current source tree exposes these package import paths:
- `gnalloy.org/codec-memcache`
- `gnalloy.org/codec-memcache/ascii`

Use `go doc` against the package that matches the behavior you need:

```bash
go doc gnalloy.org/codec-memcache
go doc gnalloy.org/codec-memcache/ascii
```

Selected current exported entry points:
- `const MagicRequest byte = 0x80 ...`
- `const DefaultFrameCodecName = "memcache-frame-codec" ...`
- `const HeaderLength = 24`
- `var ErrInvalidFrame = errors.New("gnalloy/codec/memcache: invalid frame") ...`
- `func AddClientCodec(pipeline *channel.Pipeline, maxFrameLength int) error`
- `func AddNamedClientCodec(pipeline *channel.Pipeline, frameName string, objectName string, ...) error`
- `type Command string`
- `type Request struct{ ... }`
- `type RequestDecoder struct{ ... }`
- `type RequestEncoder struct{}`
- `type Response struct{ ... }`
- `type ResponseDecoder struct{ ... }`

## Example 3: Use Executable Tests as Behavioral Examples

Repository tests are executable examples of supported behavior. Start with the selected names below, then read the matching `_test.go` files for complete setup and assertions. See [Testing and Performance](testing.md) for the complete discovered list.

```bash
GOWORK=off GOTOOLCHAIN=local go test ./... -run Test -count=1
```

Selected current test, benchmark, fuzz, and example entry points:
- `BenchmarkFrameDecoder`
- `TestAddClientCodecRejectsInvalidPipeline`
- `TestClientCodecInboundResponseDecodesObject`
- `TestClientCodecOutboundRequestEncodesFrame`
- `TestFrameDecoderParsesBinaryRequestZeroCopyParts`
- `TestFrameDecoderParsesFragmentedBinaryHeader`
- `TestFrameEncoderWritesHeaderAndBodyParts`
- `TestObjectAggregatorConvertsRequestFrame`
- `TestObjectAggregatorReportsTooLongBody`
- `TestRequestDecoderParsesStorageCommand`
- `TestRequestEncoderWritesRetrievalAndStorageCommands`
- `TestResponseDecoderParsesMultiValueResponse`
- `TestServerCodecInboundRequestAndOutboundResponse`

## Example 4: Cross-Module Assembly

Direct Gnalloy dependencies for this module:
- `gnalloy.org/gnalloy`

Assembly guidance:
- Use this codec above a byte-oriented or datagram transport and below application handlers.
- The codec converts bytes or Gnalloy messages into protocol objects and converts outbound protocol objects back to bytes.
- It does not open sockets, own EventLoops, or define application lifecycle.

## Example 5: Pressure-Test Harness

For sustained load, wire this module into a scenario under `gnalloy.org/benchmarks` or a runnable client under `gnalloy.org/examples` when the module participates in network traffic. Record host, OS, CPU, Go version, protocol, payload, concurrency, warmup, repetitions, throughput, and p99 latency in the report.
