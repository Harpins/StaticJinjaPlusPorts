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

ADD --checksum=sha256:3555bcfd670e134e8360ad934cb5bad1bbe2a7dad24ba7cafa0a3bb8b23c6444 \
    https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.0.tar.gz \
    /tmp/source.tar.gz

RUN tar -xzf /tmp/source.tar.gz -C /app --strip-components=1 && \
    rm /tmp/source.tar.gz && \
    pip install --no-cache-dir -r requirements.txt

LABEL org.opencontainers.image.title="StaticJinjaPlus 0.1.0" \
      org.opencontainers.image.description="Static site generator based on Jinja2" \
      org.opencontainers.image.version="0.1.0" \
      org.opencontainers.image.source="https://github.com/MrDave/StaticJinjaPlus"

ENTRYPOINT ["python", "main.py", "--srcpath"]
CMD ["templates_example"]