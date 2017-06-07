FROM s390x/ubuntu

RUN apt-get update && apt-get install -y \
    curl \
    nodejs-legacy \
    git

RUN git clone https://github.com/mrvautin/adminMongo.git

WORKDIR adminMongo

RUN npm install

EXPOSE 1234

CMD node app
