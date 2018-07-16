# Dockerfile that builds a release of gollvm from the tip (master)
# see https://go.googlesource.com/gollvm/+/master#setting-up-a-gollvm-work-area
# note that intermediate steps are preserved, so the image is going to be on the big side
# gollvm is installed in $GOLLVM_PATH and is added to the PATH, so you can simply run `go`

FROM ubuntu

RUN apt-get update && \
    apt-get install --no-install-recommends -y git ninja-build cmake build-essential gcc autoconf && \
    rm -rf /var/lib/apt/lists/*

RUN mkdir -p /gollvm/src /gollvm/build /gollvm/install

RUN cd /gollvm/src && git clone http://llvm.org/git/llvm.git
RUN cd /gollvm/src/llvm/tools && git clone https://go.googlesource.com/gollvm
RUN cd /gollvm/src/llvm/tools/gollvm && git clone https://go.googlesource.com/gofrontend
RUN cd /gollvm/src/llvm/tools/gollvm/libgo && git clone https://github.com/libffi/libffi.git
RUN cd /gollvm/src/llvm/tools/gollvm/libgo && git clone https://github.com/ianlancetaylor/libbacktrace.git

RUN cd /gollvm/build && \
    cmake -DCMAKE_INSTALL_PREFIX=/gollvm/install -DCMAKE_BUILD_TYPE=Release -DLLVM_USE_LINKER=gold -G Ninja ../llvm \
    ninja gollvm \
    ninja install-gollvm

ENV GOLLVM_PATH=/gollvm/install
ENV LD_LIBRARY_PATH=$GOLLVM_PATH/lib64
ENV PATH=$GOLLVM_PATH/bin:$PATH
