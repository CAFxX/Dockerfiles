# `gollvm` minimal image
[![docker stars](https://img.shields.io/docker/stars/cafxx/gollvm.svg)](https://hub.docker.com/r/cafxx/gollvm-minimal/)
[![docker pulls](https://img.shields.io/docker/pulls/cafxx/gollvm.svg)](https://hub.docker.com/r/cafxx/gollvm-minimal/)
[![docker status](https://img.shields.io/docker/build/cafxx/gollvm.svg)](https://hub.docker.com/r/cafxx/gollvm-minimal/builds/)

## Usage
Use `cafxx/gollvm-minimal` as your base image: the `go` command is on the `PATH` and maps to [`gollvm`](https://go.googlesource.com/gollvm)

```
FROM cafxx/gollvm-minimal
RUN go get <go-package-import>
RUN go build -gogccflags="-static" <go-package-import>
```

## Notes
- `gollvm` does not have stable releases yet; this image is built from the head of master of both LLVM and gollvm.
- This image is the build output-only version of the [`gollvm`](../gollvm) builder image. If you want to *build* gollvm, please use [`gollvm`](../gollvm) instead.
