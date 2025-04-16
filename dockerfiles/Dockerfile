FROM ghcr.io/taffish-org/r:4.4.3

LABEL maintainer="taffish@163.com"

WORKDIR /workspace

RUN apt-get update && apt-get install -y git python3 && \
    install2.r --error --repos 'https://cran.rstudio.com' minpack.lm argparse && \
    cd / && git clone https://github.com/tbenavi1/genomescope2.0.git && \
    cd /genomescope2.0/ && Rscript /genomescope2.0/install.R && \
    echo '#!/bin/sh' > /usr/local/bin/genomescope && \
    echo 'Rscript /genomescope2.0/genomescope.R $@' >> /usr/local/bin/genomescope && \
    chmod +x /usr/local/bin/genomescope

ENV PATH=/genomescope2.0/:{$PATH}

ENV TAFFISH_ENV=TAFFISH
ENV TAFFISH_NAME=genomescope
