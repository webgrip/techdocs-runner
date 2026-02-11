FROM webgrip/techdocs-builder:latest@sha256:3c33b23bdb7188de8ff9ed55b7181db3141200c5615547944154e2eadfac9b56 AS techdocs

RUN apk add --no-cache \
    python3 \
    py3-pip

COPY --from=webgrip/techdocs-builder@sha256:3c33b23bdb7188de8ff9ed55b7181db3141200c5615547944154e2eadfac9b56 /usr/local /usr/local
COPY --from=webgrip/techdocs-builder@sha256:3c33b23bdb7188de8ff9ed55b7181db3141200c5615547944154e2eadfac9b56 /opt/plantuml.jar /opt/plantuml.jar
COPY --from=webgrip/techdocs-builder@sha256:3c33b23bdb7188de8ff9ed55b7181db3141200c5615547944154e2eadfac9b56 /usr/local/bin/plantuml /usr/local/bin/plantuml

COPY ./ops/docker/techdocs-runner/docker-entrypoint.sh ./docker-entrypoint.sh

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["mkdocs", "serve", "-a", "0.0.0.0:8000"]

