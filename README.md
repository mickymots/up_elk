# Setup ELK With SSL

## Setup Certs 
Steps:

1. Generate the certificates (only needed once):

    docker-compose -f create-certs.yml run --rm create_certs

2. Start two Elasticsearch nodes configured for SSL/TLS:



docker-compose up -d

## Test the setup

3. Access the Elasticsearch API over SSL/TLS using the bootstrapped password:

docker run --rm -v es_certs:/certs --network=es_default docker.elastic.co/elasticsearch/elasticsearch:7.6.2 curl --cacert /certs/ca/ca.crt -u elastic:PleaseChangeMe https://es01:9200

