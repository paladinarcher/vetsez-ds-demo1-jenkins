FROM jenkins/jnlp-slave:alpine

USER root

# Install Docker
RUN apk add python-dev libffi-dev openssl-dev gcc libc-dev make
RUN apk add --no-cache docker

# Install docker-compose
RUN apk add py-pip && \
    pip install docker-compose

USER jenkins