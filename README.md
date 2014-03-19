# go-websocket-frames #

[![Build
Status](https://drone.io/github.com/tchap/go-websocket-frames/status.png)](https://drone.io/github.com/tchap/go-websocket-frames/latest)

A codec for [websocket](http://godoc.org/code.google.com/p/go.net/websocket)
for exchanging multi-part binary messages.

## Protocol ##

```
+-------------------------------------+
| LEN = number of frames (uint32, BE) |
+-------------------------------------+-----------------------+
| N = frame size (uint32, BE)         | frame (N bytes long)  |
+-------------------------------------+-----------------------+
| (LEN-1) frames follow               | ...                   |
```

## Example ##

```go
import "github.com/tchap/go-websocket-frames/frames"

// Sender
data := [][]byte{
	[]byte("first"),
	[]byte("second"),
	[]byte("third"),
	[]byte("fourth"),
	[]byte("fifth"),
}
frames.C.Send(conn, data)

// Receiver
var data [][]byte
frames.C.Receive(conn, &data)
```

## Documentation ##

See the generated documentation at
[GoDoc](http://godoc.org/github.com/tchap/go-websocket-frames/frames).

## License ##

MIT, see the `LICENSE` file.
