# Pack binaries with upx

Go binaries while statically built can grow quite quickly in size.
One method of trying to shrink them down is to pack them with one of available
"executable packers" like [upx](https://upx.github.io/).

For instance the following Go program:

```go
package main

func main() {
	print("Hello world")
}
```

Compiled on Mac OS with `go 1.14.2` results in a binary 1200912 bytes in size.

Packed with `upx v3.96` with compression level 9 yields a binary 655376 in size
which is a 54.57% compression ration.

Going further and using `--brute` option we get a binary 589840 in size
which is a 49.12% compression ration.
