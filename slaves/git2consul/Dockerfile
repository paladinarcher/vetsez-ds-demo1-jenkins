FROM jenkins/jnlp-slave:3.27-1-alpine

USER root

# Install curl
RUN apk add --no-cache npm

# Install git2consul
RUN npm install -g git2consul

USER jenkins