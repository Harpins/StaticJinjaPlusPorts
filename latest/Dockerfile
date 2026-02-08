FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        python3 \
        python3-pip \
        python3-venv \
    && apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN python3 -m venv /venv
ENV PATH="/venv/bin:$PATH"

WORKDIR /app

ADD --checksum=sha256:9adccb8fe17a40252df1a3acdea7edef4633b4ecaa8ba2dd5e0270f87ae43eab \
    https://github.com/MrDave/StaticJinjaPlus/archive/refs/heads/main.tar.gz \
    /tmp/source.tar.gz

RUN tar -xzf /tmp/source.tar.gz -C /app --strip-components=1 && \
    rm /tmp/source.tar.gz && \
    pip install --no-cache-dir -r requirements.txt

LABEL org.opencontainers.image.title="StaticJinjaPlus latest" \
      org.opencontainers.image.description="Static site generator based on Jinja2" \
      org.opencontainers.image.version="latest" \
      org.opencontainers.image.source="https://github.com/MrDave/StaticJinjaPlus"

ENTRYPOINT ["python", "main.py", "--srcpath"]
CMD ["templates_example"]