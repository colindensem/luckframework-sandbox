ARG VARIANT=0.35.1
FROM crystallang/crystal:${VARIANT}

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && \
    apt update && apt install -y \
    gnupg tmux bash postgresql-client nodejs yarn wget curl \
    chromium-chromedriver chromium-browser \
    libgconf-2-4 libreadline-dev && \
    # Cleanup leftovers
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

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

# Set the environment variables for the Chromium browser.
ENV CHROME_BIN=/usr/bin/chromium-browser \
    CHROME_PATH=/usr/lib/chromium/

EXPOSE 5000
