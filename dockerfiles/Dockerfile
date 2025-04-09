FROM ghcr.io/taffish-org/r:4.4.3

LABEL maintainer="taffish@163.com"

WORKDIR /workspace

RUN apt-get update && apt-get install -y git && \
    cd / && git clone https://github.com/schatzlab/genomescope && \
    echo '#!/bin/sh' > /usr/local/bin/genomescope && \
    echo 'Rscript /genomescope/genomescope.R' >> /usr/local/bin/genomescope && \
    chmod +x /usr/local/bin/genomescope

ENV TAFFISH_ENV=TAFFISH
ENV TAFFISH_NAME=genomescope
