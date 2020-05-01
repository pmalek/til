# Prune Go binaries from debug symbols

`go build` accepts `-ldflags` parameter which is passed down to `go` linker.
Two of [those flags](https://golang.org/cmd/link/#hdr-Command_Line) that you can
provide are:

* `-w` to `Omit the DWARF symbol table.`
* `-s` to `Omit the symbol table and debug information.`

This can help when one wants to shrink the resultant binary size.

Visit [https://golang.org/cmd/link](https://golang.org/cmd/link) for more details.
