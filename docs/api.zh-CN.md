# API 参考

[English](api.md) | [文档索引](README.zh-CN.md)

本清单由本仓库 package 的 `go doc -short` 生成，用于快速查看公共面。精确语义以源码和测试为准。

## 包

### `gnalloy.org/codec-memcache`

包名：`memcache`

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

包名：`ascii`

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
