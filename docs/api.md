# API Reference

[简体中文](api.zh-CN.md) | [Docs Index](README.md)

This inventory is generated from `go doc -short` for the packages in this repository. It is a quick public-surface map; source files and tests remain the authority for exact semantics.

## Packages

### `gnalloy.org/codec-memcache`

Package name: `memcache`

```text
const MagicRequest byte = 0x80 ...
const DefaultFrameCodecName = "memcache-frame-codec" ...
const HeaderLength = 24
var ErrInvalidFrame = errors.New("gnalloy/codec/memcache: invalid frame") ...
func AddClientCodec(pipeline *channel.Pipeline, maxFrameLength int) error
func AddNamedClientCodec(pipeline *channel.Pipeline, frameName string, objectName string, ...) error
func AddNamedServerCodec(pipeline *channel.Pipeline, frameName string, objectName string, ...) error
func AddServerCodec(pipeline *channel.Pipeline, maxFrameLength int) error
func NewFrameCodec(maxFrameLength int) (channel.Handler, error)
type ClientCodec struct{ ... }
    func NewClientCodec() *ClientCodec
type Frame struct{ ... }
    func NewRequest(opcode Opcode, extras buffer.ByteBuf, key buffer.ByteBuf, value buffer.ByteBuf) Frame
    func NewResponse(opcode Opcode, status Status, extras buffer.ByteBuf, key buffer.ByteBuf, ...) Frame
type FrameDecoder struct{ ... }
    func NewFrameDecoder(maxFrameLength int) (*FrameDecoder, error)
type FrameEncoder struct{}
    func NewFrameEncoder() *FrameEncoder
type FullRequest = Request
type FullResponse = Response
type ObjectAggregator struct{ ... }
    func NewObjectAggregator(maxContentLength int) (*ObjectAggregator, error)
type Opcode byte
    const OpcodeGet Opcode = 0x00 ...
type Request struct{ ... }
    func NewFullRequest(opcode Opcode, extras buffer.ByteBuf, key buffer.ByteBuf, value buffer.ByteBuf) Request
type Response struct{ ... }
    func NewFullResponse(opcode Opcode, status Status, extras buffer.ByteBuf, key buffer.ByteBuf, ...) Response
type ServerCodec struct{ ... }
    func NewServerCodec() *ServerCodec
type Status uint16
    const StatusOK Status = 0x0000 ...
```

### `gnalloy.org/codec-memcache/ascii`

Package name: `ascii`

```text
type Command string
    const CommandGet Command = "get" ...
type Request struct{ ... }
type RequestDecoder struct{ ... }
    func NewRequestDecoder(maxLineBytes int, maxValueBytes int) (*RequestDecoder, error)
type RequestEncoder struct{}
    func NewRequestEncoder() *RequestEncoder
type Response struct{ ... }
type ResponseDecoder struct{ ... }
    func NewResponseDecoder(maxLineBytes int, maxValueBytes int) (*ResponseDecoder, error)
type ResponseEncoder struct{}
    func NewResponseEncoder() *ResponseEncoder
type Status string
    const StatusStored Status = "STORED" ...
type Value struct{ ... }
```
