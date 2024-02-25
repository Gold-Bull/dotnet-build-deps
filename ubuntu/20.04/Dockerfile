# syntax=docker/dockerfile:1
FROM ghcr.io/gold-bull/dotnet-ubuntu-base:ubuntu-20.04-latest

ARG DEBIAN_FRONTEND=noninteractive
ARG BUILD_DEPS_SCRIPT=https://gist.githubusercontent.com/SaileshBellamkonda/7a0fe00e2b999b56e9a77891df0cae84/raw/dotnet-build-s390x-ubt-2004.sh

RUN --security=insecure set -ex; \
    apt-get update; \
    apt-get install -y curl bash; \
    curl -L -o - $BUILD_DEPS_SCRIPT | bash -;
