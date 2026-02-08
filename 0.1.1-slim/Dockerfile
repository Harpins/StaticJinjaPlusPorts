FROM python:3.10-slim

ENV PYTHONUNBUFFERED=1

WORKDIR /app

ADD --checksum=sha256:30d9424df1eddb73912b0e2ad5375fa2c876c8e30906bec91952dfb75dcf220b \
    https://github.com/MrDave/StaticJinjaPlus/archive/refs/tags/0.1.1.tar.gz \
    /tmp/source.tar.gz

RUN tar -xzf /tmp/source.tar.gz -C /app --strip-components=1 && \
    rm /tmp/source.tar.gz && \
    pip install --no-cache-dir -r requirements.txt

LABEL org.opencontainers.image.title="StaticJinjaPlus 0.1.1 slim" \
      org.opencontainers.image.description="Static site generator based on Jinja2 (slim)" \
      org.opencontainers.image.version="0.1.1-slim" \
      org.opencontainers.image.source="https://github.com/MrDave/StaticJinjaPlus"

ENTRYPOINT ["python", "main.py", "--srcpath"]
CMD ["templates_example"]