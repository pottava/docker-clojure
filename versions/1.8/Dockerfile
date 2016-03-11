# Clojure v1.8
# docker run --rm pottava/clojure lein --version
# docker run --rm -v `pwd`:/app pottava/clojure lein new project
# docker run --rm -v `pwd`/project:/app pottava/clojure lein test

FROM pottava/java:8

ENV CLOJURE_VERSION=1.8.0 \
    LEIN_ROOT=yes

RUN set -ex \
      && apk --no-cache add --virtual build-dependencies curl unzip \
      && apk --no-cache add bash \
      && mkdir -p /usr/lib/clojure \
      && cd /usr/lib/clojure \
      && curl -O --location --silent --show-error http://repo1.maven.org/maven2/org/clojure/clojure/${CLOJURE_VERSION}/clojure-${CLOJURE_VERSION}.zip \
      && curl -O --location --silent --show-error https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein \
      && mv lein /usr/bin/ \
      && chmod +x /usr/bin/lein \
      && lein \
      && unzip -q clojure-${CLOJURE_VERSION}.zip \
      && rm -rf clojure-${CLOJURE_VERSION}.zip \
          clojure-${CLOJURE_VERSION}/changes.md \
          clojure-${CLOJURE_VERSION}/doc \
          clojure-${CLOJURE_VERSION}/epl-v10.html \
          clojure-${CLOJURE_VERSION}/readme.txt \
          clojure-${CLOJURE_VERSION}/src \
          clojure-${CLOJURE_VERSION}/test \
      && apk del --purge build-dependencies

VOLUME /app
WORKDIR /app
