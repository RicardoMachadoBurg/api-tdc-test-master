FROM anapsix/alpine-java

RUN apk add --update curl && \
    rm -rf /var/cache/apk/*

ENV WIREMOCK_PACKAGE wiremock
ARG WIREMOCKM_VERSION=2.23.2

RUN mkdir /$WIREMOCK_PACKAGE
WORKDIR /$WIREMOCK_PACKAGE
RUN curl -sSL -o $WIREMOCK_PACKAGE.jar https://repo1.maven.org/maven2/com/github/tomakehurst/$WIREMOCK_PACKAGE-standalone/$WIREMOCKM_VERSION/$WIREMOCK_PACKAGE-standalone-$WIREMOCKM_VERSION.jar

ADD __files /wiremock/__files
ADD mappings /wiremock/mappings

EXPOSE 8080

ENTRYPOINT ["java","-jar","wiremock.jar","--verbose"]
