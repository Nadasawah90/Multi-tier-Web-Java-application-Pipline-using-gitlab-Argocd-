FROM maven:3.9.6-eclipse-temurin-17 AS build_image

RUN apt update && apt install git -y

RUN git clone https://github.com/devopshydclub/vprofile-project.git

WORKDIR /vprofile-project

RUN git checkout docker && mvn clean install

FROM tomcat:8-jre11

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=build_image /vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080

CMD ["catalina.sh", "run"]
