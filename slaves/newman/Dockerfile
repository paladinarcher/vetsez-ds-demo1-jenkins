FROM jenkins/jnlp-slave:alpine

USER root

# Install NodeJS and NPM
RUN apk add --update nodejs npm

# Install Newman
RUN npm install -g newman && \
    npm install -g newman-reporter-junitfull

USER jenkins