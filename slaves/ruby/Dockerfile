FROM jenkins/jnlp-slave:3.29-1
ARG MAVEN_VERSION=3.6.0
ARG JRUBY_VERSION=9.2.8.0
ARG YARN_VERSION=1.17.3

USER root

# Install Maven
ENV MAVEN_HOME /usr/lib/mvn
ENV PATH $MAVEN_HOME/bin:$PATH

RUN wget -q http://archive.apache.org/dist/maven/maven-3/$MAVEN_VERSION/binaries/apache-maven-$MAVEN_VERSION-bin.tar.gz && \
  tar -zxf apache-maven-$MAVEN_VERSION-bin.tar.gz && \
  rm apache-maven-$MAVEN_VERSION-bin.tar.gz && \
  mv apache-maven-$MAVEN_VERSION /usr/lib/mvn

# Install jRuby
ENV PATH /usr/lib/jruby-${JRUBY_VERSION}/bin:$PATH
RUN wget -q https://repo1.maven.org/maven2/org/jruby/jruby-dist/${JRUBY_VERSION}/jruby-dist-${JRUBY_VERSION}-bin.tar.gz && \
  tar -zxf jruby-dist-${JRUBY_VERSION}-bin.tar.gz && \
  rm jruby-dist-${JRUBY_VERSION}-bin.tar.gz && \
  mv jruby-${JRUBY_VERSION} /usr/lib/jruby-${JRUBY_VERSION} && \
  chown -R jenkins /usr/lib/jruby-9.2.8.0 && \
  chgrp -R jenkins /usr/lib/jruby-9.2.8.0

# Install Node
RUN curl -sL https://deb.nodesource.com/setup_12.x | bash - && \
    apt-get install -y nodejs

# Install Yarn
ENV PATH /usr/lib/yarn/bin:$PATH
RUN wget -q https://github.com/yarnpkg/yarn/releases/download/v${YARN_VERSION}/yarn-v${YARN_VERSION}.tar.gz && \
  tar -zxf yarn-v${YARN_VERSION}.tar.gz && \
  rm yarn-v${YARN_VERSION}.tar.gz && \
  mv yarn-v${YARN_VERSION} /usr/lib/yarn && \
  chown -R jenkins /usr/lib/yarn && \
  chgrp -R jenkins /usr/lib/yarn

# Install Chrome for UI Testing
RUN wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - && \
    sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list' && \
    apt-get update && \
    apt-get install -y google-chrome-stable

USER jenkins

# Install Bundler
RUN gem install bundler && \
    gem install rake
