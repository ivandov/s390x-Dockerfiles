FROM s390x/ibmnode

EXPOSE 9003

RUN apt-get update && apt-get install -y \
    wget \
    ssh \
    sudo

RUN wget https://sgmanager.ng.bluemix.net/installers/ibm-securegateway-client-1.7.1+client_s390x.deb

# Workaround for the 1.7.1 client deb overwriting /usr/local links without checking
RUN mv /usr/local/bin/* /bin/ && mv /usr/local/lib/* /lib/

RUN dpkg -i ibm-securegateway-client-1.7.1+client_s390x.deb

RUN su secgwadmin

WORKDIR /opt/ibm/securegateway/client

ENTRYPOINT node lib/secgwclient.js
