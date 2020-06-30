# Netlink

> The Netlink socket family is a Linux kernel interface used for
> inter-process communication (IPC) between both the kernel and userspace
> processes, and between different userspace processes, in a way similar
> to the Unix domain sockets. <sup>[wikipedia.org](https://en.wikipedia.org/wiki/Netlink)</sup>

It was introduced to primarily replace [`ioctl`](https://en.wikipedia.org/wiki/Ioctl).

It's used e.g. by the `iproute2` utilities which "are often recommended over
now-obsolete net-tools utilities" <sup>[wikipedia.org](https://en.wikipedia.org/wiki/Iproute2)</sup>.

To create a socket of `AF_NETLINK` type one should call `socket` in the following way:

```c
netlink_socket = socket(AF_NETLINK, socket_type, netlink_family);
```

where:

* `socket` is either `SOCK_RAW` or `SOCK_DGRAM` as both values are allowed
* `netlink_family` is one of may allowed values like e.g. `NETLINK_ROUTE` or `NETLINK_GENERIC`

More extensive documentation on the how to use netlink sockets in `C` code can
be found at <https://linux.die.net/man/7/netlink>.

There also exist implementations in many different languages including
<https://github.com/vishvananda/netlink> written in Go.

---

There's a great [lightning talk by Matt Layher from GopherCon 2018](https://www.youtube.com/watch?v=tw-9fNygYE4)
where he describes `netlink` and its families.
