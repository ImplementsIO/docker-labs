FROM elasticsearch:5

ENV ES_JAVA_OPTS="-Des.path.conf=/etc/elasticsearch"

ENV GEOLITE2_CITY="http://geolite.maxmind.com/download/geoip/database/GeoLite2-City.tar.gz"
ENV GEOLITE2_COUNTRY="http://geolite.maxmind.com/download/geoip/database/GeoLite2-Country.tar.gz"

RUN /usr/share/elasticsearch/bin/elasticsearch-plugin install -b ingest-geoip

RUN mkdir -p /usr/share/elasticsearch/config/ingest-geoip \
    && mkdir -p /tmp/geoip \
    && cd /tmp/geoip \
    && wget -O city.tar.gz "$GEOLITE2_CITY" \
    && tar -xf city.tar.gz \
    && wget -O country.tar.gz "$GEOLITE2_COUNTRY" \
    && tar -xf country.tar.gz \
    && mv **/*.mmdb /usr/share/elasticsearch/config/ingest-geoip/ \
    && rm -rf /tmp/geoip