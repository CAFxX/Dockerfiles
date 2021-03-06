# `gollvm` builder image
[![docker stars](https://img.shields.io/docker/stars/cafxx/gollvm.svg)](https://hub.docker.com/r/cafxx/gollvm/)
[![docker pulls](https://img.shields.io/docker/pulls/cafxx/gollvm.svg)](https://hub.docker.com/r/cafxx/gollvm/)
[![docker status](https://img.shields.io/docker/build/cafxx/gollvm.svg)](https://hub.docker.com/r/cafxx/gollvm/builds/)

## Usage
Use `cafxx/gollvm` as your base image: the `go` command is on the `PATH` and maps to [`gollvm`](https://go.googlesource.com/gollvm)

```
FROM cafxx/gollvm
RUN go get <go-package-import>
RUN go build -gogccflags="-static" <go-package-import>
```

## Notes
- `gollvm` does not have stable releases yet; this image is built from the head of master of both LLVM and gollvm.
- This image is very heavy (~1GB) because it is the builder stage and no attempts have been made to keep the size in check. If you want a smaller image and you are only interested in *using* gollvm, please use [`gollvm-minimal`](../gollvm-minimal) instead.
