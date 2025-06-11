ARG         python

FROM        python:3.12-alpine

ARG         cos_python_sdk_version=1.9.37
ARG         package_name=cos-python-sdk-v5-${cos_python_sdk_version}

RUN         apk add --no-cache --virtual .build-deps \
                curl \
                unzip && \
            curl -L -o zip  https://codeload.github.com/tencentyun/cos-python-sdk-v5/zip/refs/tags/V${cos_python_sdk_version} && \
            unzip zip

WORKDIR     ${package_name}

RUN         pip install setuptools && python setup.py bdist_wheel

