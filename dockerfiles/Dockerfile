FROM ghcr.io/taffish-org/r:4.4.3

LABEL maintainer="taffish@163.com"

WORKDIR /workspace

RUN apt-get update && apt-get install -y git python3 && \
    mkdir -p /usr/local/lib/R/library && \
    Rscript -e "install.packages(c('minpack.lm', 'argparse'), repos='https://cloud.r-project.org', lib='/usr/local/lib/R/library')" && \
    cd / && git clone https://github.com/tbenavi1/genomescope2.0.git && \
    cd /genomescope2.0/ && Rscript /genomescope2.0/install.R && \
    echo '#!/bin/sh' > /usr/local/bin/genomescope && \
    echo 'Rscript /genomescope2.0/genomescope.R $@' >> /usr/local/bin/genomescope && \
    chmod +x /usr/local/bin/genomescope

ENV R_LIBS=/usr/local/lib/R/library
ENV PATH=/genomescope2.0/:{$PATH}

ENV TAFFISH_ENV=TAFFISH
ENV TAFFISH_NAME=genomescope
