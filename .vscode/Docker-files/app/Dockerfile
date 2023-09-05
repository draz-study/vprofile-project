FROM openjdk:11 AS  BUILD_IMAGE
RUN apt update -y && apt install maven -y
RUN git clone https://github.com/draz-study/vprofile-project.git
RUN cd vprofile-project && git checkout docket && mvn install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

LABEL "Poject"="Vprofile"
LABEL "Author"="DanRaz"

EXPOSE 8080
CMD ["catalina.sh", "run"]