ARG BUILD_FROM
FROM ${BUILD_FROM}

ARG LSB_RELEASE=bookworm

SHELL ["/bin/bash", "-o", "pipefail", "-c"]

# Install SNClient
RUN curl -v "https://labs.consol.de/repo/stable/RPM-GPG-KEY" -o /etc/apt/auth.conf.d/labs.consol.de-RPM-GPG-KEY
RUN echo "deb [signed-by=/etc/apt/auth.conf.d/labs.consol.de-RPM-GPG-KEY] http://labs.consol.de/repo/testing/debian ${LSB_RELEASE} main" > /etc/apt/sources.list.d/labs-consol-testing.list
RUN apt-get update -y
RUN apt-get install snclient -y

EXPOSE 8443

# Copy data for add-on
COPY run.sh /
RUN chmod +x /run.sh

CMD [ "/run.sh" ]
