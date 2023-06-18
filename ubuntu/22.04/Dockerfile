# syntax=docker/dockerfile:labs

FROM ubuntu

ARG DEBIAN_FRONTEND=noninteractive
ARG BUILD_DEPS_SCRIPT=https://gist.githubusercontent.com/SaileshBellamkonda/e050c6f8283c07b99329a405c837b22d/raw/dotnet-build-s390x-ubt-2204.sh

RUN --security=insecure set -ex; \
    apt-get update; \
    apt-get install -y curl bash; \
    curl -L -o - $BUILD_DEPS_SCRIPT | bash -;
