ARG         python

FROM        python:${python}-alpine3.16

ARG         grpc_version
ARG         REPO_ROOT=grpc

ENV         grpc_version=${grpc_version}
ENV         REPO_ROOT=grpc

RUN         apk add --no-cache --virtual .build-deps \
                build-base \
                g++ \
                musl-dev \
                libffi-dev \
                g++ \
                git && \
            git clone -b v$grpc_version https://github.com/grpc/grpc $REPO_ROOT

WORKDIR     $REPO_ROOT

RUN         git submodule update --init && \
            pip install -r requirements.txt && \
            GRPC_PYTHON_BUILD_WITH_CYTHON=1 pip install . && \
            python setup.py -q sdist bdist_wheel
