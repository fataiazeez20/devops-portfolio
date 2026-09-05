FROM nginx:1.29-alpine

LABEL org.opencontainers.image.source="https://github.com/fataiazeez20/devops-portfolio"

RUN rm -rf /usr/share/nginx/html/*

COPY index.html /usr/share/nginx/html/index.html
COPY style.css /usr/share/nginx/html/style.css

COPY images/ /usr/share/nginx/html/images/

EXPOSE 80

HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
    CMD wget --no-verbose --tries=1 --spider http://127.0.0.1/ || exit 1
