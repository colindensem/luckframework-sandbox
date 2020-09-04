ARG VARIANT=0.35.1
FROM crystallang/crystal:${VARIANT}-alpine
RUN apk update \
    && apk add --no-cache gnupg tmux bash postgresql-client nodejs yarn openssh

RUN cd /tmp \
    && git clone https://github.com/luckyframework/lucky_cli \
    && cd lucky_cli \
    && git checkout v0.23.0 \
    && shards install \
    && crystal build src/lucky.cr \
    && mv lucky /usr/local/bin \
    && rm -rf /tmp/luckly_cli \
    && cd /tmp \
    && wget https://github.com/DarthSim/overmind/releases/download/v2.2.0/overmind-v2.2.0-linux-amd64.gz \
    && gunzip -d overmind-v2.2.0-linux-amd64.gz \
    && chmod a+x overmind-v2.2.0-linux-amd64 \
    && mv overmind-v2.2.0-linux-amd64 /usr/local/bin/overmind

EXPOSE 5000
