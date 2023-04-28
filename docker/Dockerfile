FROM amazoncorretto:17
LABEL maintainer="viktor@sadovnikov.info"

ADD sample-app.jar /

EXPOSE 8080
ENTRYPOINT ["/usr/bin/java", "-jar", "sample-app.jar"]
