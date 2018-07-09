# Yair

ENV REGISTRY_HOST="registry.hub.docker.com"
ENV CLAIR_HOST="clair:6060"
ENV OUTPUT_FORMAT="table"
ENV FAIL_ON_SCORE="824"
ENV ANALYZE_CONTAINER=""

# Klar

list of environment variables and its default

ENV CLAIR_ADDR='clair'
ENV CLAIR_OUTPUT='Unknown'
ENV CLAIR_THRESHOLD='0'
ENV DOCKER_USER=''
ENV DOCKER_PASSWORD=''
ENV DOCKER_INSECURE='false'
ENV REGISTRY_INSECURE='false'
ENV JSON_OUTPUT='false'

custom settings

ENV CLAIR_ADDR='clair'
ENV CLAIR_OUTPUT='High'
ENV CLAIR_THRESHOLD='1'
ENV CLAIR_TIMEOUT='3'
ENV DOCKER_USER=''
ENV DOCKER_PASSWORD=''
ENV DOCKER_INSECURE='false'
ENV REGISTRY_INSECURE='false'
ENV JSON_OUTPUT='false'

* CLAIR_OUTPUT: HighがあればNGとしたいため、これ以上のレベルの脆弱性をカウントする
* CLAIR_THRESHOLD: High以上が1つでもあればNGとする
* TIMEOUT: layerが増えるにつれ、defaultの1分ではタイムアウトが見られた
