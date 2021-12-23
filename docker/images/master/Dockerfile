FROM python:3.4-slim

MAINTAINER Alberto Martín <alberto.martin@bitergia.com>

ENV GIT_URL_PERCEVAL https://github.com/grimoirelab/perceval.git
ENV GIT_REV_PERCEVAL master
ENV BUILD_PACKAGES build-essential

# install dependencies

RUN apt update && \
    apt install -y build-essential git --no-install-recommends && \
    git clone --depth 1 https://github.com/grimoirelab/perceval.git -b master && \
    pip3 install -r perceval/requirements.txt perceval/ && \
    apt remove --purge -y build-essential && \
    apt clean && \
    apt autoremove --purge -y
    #find /var/lib/apt/lists -type f -delete

ENTRYPOINT ["/usr/local/bin/perceval"]
