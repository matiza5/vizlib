FROM debian:bullseye AS cert-source
WORKDIR /tmp/
RUN apt-get update && \
    apt-get install -y openssl && \
    openssl genrsa -out ssl.key 2048 && \
    openssl req -new -key ssl.key -out ssl.csr \
        -subj "/C=PL/ST=MAZ/L=Warsaw/O=OrgName/OU=IT Department/CN=www.example.com" && \
    openssl x509 -req -days 365 -in ssl.csr -signkey ssl.key -out ssl.crt && \
    cat ssl.key ssl.crt >> ssl.pem

FROM haproxy:2.7-alpine
COPY haproxy.cfg /usr/local/etc/haproxy/
COPY --from=cert-source /tmp/ssl.pem /usr/local/etc/haproxy/
