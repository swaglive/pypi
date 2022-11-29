ARG         python

FROM        python:${python}-alpine3.16

ARG         MAKEFLAGS
ARG         protobuf_version=3.20.3
ARG         python_protobuf_version=3.20.3

ENV         MAKEFLAGS=${MAKEFLAGS}

RUN         apk add --no-cache --virtual .build-deps \
                curl \
                zlib-dev \
                build-base \
                cmake \
                libtool && \
            curl -sfL https://github.com/protocolbuffers/protobuf/releases/download/v${protobuf_version}/protobuf-python-${python_protobuf_version}.tar.gz | tar xz

WORKDIR     protobuf-${python_protobuf_version}

RUN         ./configure CFLAGS=-fPIC CXXFLAGS=-fPIC && \
            make && \
            make install && \
            cd python && \
            python setup.py bdist_wheel --cpp_implementation --compile_static_extension