FROM webgrip/techdocs-builder:latest AS techdocs

RUN apk add --no-cache \
    python3 \
    py3-pip

COPY --from=webgrip/techdocs-builder /usr/local /usr/local
COPY --from=webgrip/techdocs-builder /opt/plantuml.jar /opt/plantuml.jar
COPY --from=webgrip/techdocs-builder /usr/local/bin/plantuml /usr/local/bin/plantuml

COPY ./ops/docker/techdocs-runner/docker-entrypoint.sh ./docker-entrypoint.sh

ENTRYPOINT ["docker-entrypoint.sh"]
CMD ["mkdocs", "serve", "-a", "0.0.0.0:8000"]
