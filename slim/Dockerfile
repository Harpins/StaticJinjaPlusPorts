FROM python:3.10-slim

ENV PYTHONUNBUFFERED=1

WORKDIR /app

ADD --checksum=sha256:9adccb8fe17a40252df1a3acdea7edef4633b4ecaa8ba2dd5e0270f87ae43eab \
    https://github.com/MrDave/StaticJinjaPlus/archive/refs/heads/main.tar.gz \
    /tmp/source.tar.gz

RUN tar -xzf /tmp/source.tar.gz -C /app --strip-components=1 && \
    rm /tmp/source.tar.gz && \
    pip install --no-cache-dir -r requirements.txt

LABEL org.opencontainers.image.title="StaticJinjaPlus latest slim" \
      org.opencontainers.image.description="Static site generator based on Jinja2 (slim)" \
      org.opencontainers.image.version="latest-slim" \
      org.opencontainers.image.source="https://github.com/MrDave/StaticJinjaPlus"

ENTRYPOINT ["python", "main.py", "--srcpath"]
CMD ["templates_example"]