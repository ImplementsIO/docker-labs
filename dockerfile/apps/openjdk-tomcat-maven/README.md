Alpine Openjdk & Tomcat & Maven Image

## Version

- JAVA_VERSION 8u92
- TOMCAT_VERSION 8.5.6
- MAVEN_VERSION 3.3.9

## Usage

```
FROM thonatos/openjdk-tomcat-maven:jdk8-maven3

# Init
RUN mkdir /app
WORKDIR /app
COPY ./ /app

RUN chmod a+x /app/compile.sh
RUN /app/compile.sh
```