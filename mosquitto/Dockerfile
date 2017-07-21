FROM alpine:3.5
MAINTAINER yurii.kyrychynskyi@globallogic.com

LABEL Description="Mosquitto MQTT Broker"

RUN apk --no-cache add mosquitto=1.4.12-r0 && \
    mkdir -p /mosquitto/data /mosquitto/certs /mosquitto/conf.d 
#    chown -R mosquitto:mosquitto /mosquitto

WORKDIR /mosquitto

EXPOSE 8883 18883

COPY docker-entrypoint.sh /

COPY mosquitto.conf passwd ./
ADD conf.d/ ./conf.d/
ADD certs/ ./certs/
ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["/usr/sbin/mosquitto", "-c", "./mosquitto.conf"]
