FROM node:14-slim
ENV DEBIAN_FRONTEND=noninteractive

# Stuur buster naar archive.debian.org
RUN sed -i -e 's|deb.debian.org|archive.debian.org|g' \
           -e 's|security.debian.org|archive.debian.org/debian-security|g' /etc/apt/sources.list \
 && printf 'Acquire::Check-Valid-Until "false";\n' > /etc/apt/apt.conf.d/99no-check-valid \
 && apt-get update \
 && apt-get install -y --no-install-recommends python3 python-is-python3 build-essential ca-certificates \
 && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /workspace/node_modules
COPY ["./dist", "./package.json", "/workspace/"]

