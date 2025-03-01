# mit-scheme-kernel

Jupyter Kernel for MIT Scheme

![](demo.png)

## Installation

### Docker

[Kevin Kwok](https://github.com/antimatter15) published a [docker image](https://hub.docker.com/r/kkwok/jupyter-mit-scheme/) that does all the things:

```
docker run -it --rm -p 8888:8888 kkwok/jupyter-mit-scheme
```

### Source

First get MIT Scheme:

```
$ wget https://ftp.gnu.org/gnu/mit-scheme/stable.pkg/10.1.5/mit-scheme-10.1.5-x86-64.tar.gz
$ tar xvf mit-scheme-10.1.5-x86-64.tar.gz
$ cd mit-scheme-10.1.5/src/
$ ./configure
$ make compile-microcode
$ sudo make install
```

Then get ZeroMQ:

```
$ wget https://github.com/zeromq/libzmq/releases/download/v4.3.1/zeromq-4.3.1.tar.gz
$ tar xvf zeromq-4.3.1.tar.gz
$ cd zeromq-4.3.1/
$ ./configure
$ make
$ sudo make install
```

And finally

```
$ git clone https://github.com/joeltg/mit-scheme-kernel
$ cd mit-scheme-kernel
$ make
$ sudo make install
$ jupyter console --kernel mit-scheme
Jupyter console 6.0.0

MIT Scheme Kernel


In [1]: (fold-left cons '() (iota 4))
Out[1]: ((((() . 0) . 1) . 2) . 3)
```

Building on macOS may require adding a `-undefined dynamic_lookup` flag to the makefile in the line that builds `zmq-shim.so`.
