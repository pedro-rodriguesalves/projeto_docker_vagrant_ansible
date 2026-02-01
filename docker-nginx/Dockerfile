FROM nginx:latest

RUN apt-get update && \
    apt-get install -y iputils-ping curl && \
    rm -rf /var/lib/apt/lists/*

COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 8080

