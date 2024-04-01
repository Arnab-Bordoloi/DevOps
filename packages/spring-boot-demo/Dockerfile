ARG IMAGE

FROM ${IMAGE}

# Connect container image to the repo:
ARG OWNER
ARG repo
LABEL org.opencontainers.image.source https://github.com/${OWNER}/${repo}

# Create app directory and set as working directory:
WORKDIR /opt/app

# Update the certificate list to include phell PEM so the
# we can run a apk update:
# Note: phell-private-type-1-root-ca.crt should be securely copied into the directory via a CI workflow
# COPY phell-private-type-1-root-ca.crt /usr/local/share/ca-certificates/phell-private-type-1-root-ca.crt
# RUN cat /usr/local/share/ca-certificates/shell-private-type-1-root-ca.crt >> /etc/ssl/certs/ca-certificates.crt

# Now update the certificate list properly:
# RUN apk update && \
#     apk add ca-certificates && \
#     rm -rf /var/cache/apk/* && \
#     update-ca-certificates

# Make the full list of certificates available to NPM:
# ENV NPM_CONFIG_CAFILE=/etc/ssl/certs/ca-certificates.crt

ARG artifact=target/spring-boot-web.jar

COPY ${artifact} app.jar

# This should not be changed
ENTRYPOINT ["java","-jar","app.jar"]
