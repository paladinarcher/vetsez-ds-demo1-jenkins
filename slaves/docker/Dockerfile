FROM jenkins/jnlp-slave:3.27-1-alpine

USER root

# Install Docker
RUN apk add --no-cache docker

# Install docker-compose
RUN apk add py-pip && \
    pip install docker-compose

USER jenkins