FROM jenkins/jnlp-slave:3.29-1

USER root

# Install VA Trusted Certificates
RUN mkdir -p /usr/local/share/ca-certificates/va
COPY ./ca-certs/*.crt /usr/local/share/ca-certificates/va/
RUN update-ca-certificates

# Insall Certs into Java Trusted keystore
RUN for file in $(ls /usr/local/share/ca-certificates/va/*.crt); \
    do keytool -importcert -alias $file -keystore "$JAVA_HOME/jre/lib/security/cacerts" -noprompt -storepass changeit -file $file; \
    done

USER jenkins
