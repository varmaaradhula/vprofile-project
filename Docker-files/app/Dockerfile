FROM openjdk:11 AS BUILD_IMG
RUN apt update && apt install maven -y
RUN git clone git@github.com:varmaaradhula/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMG vprofile-project/target/vprofile-v2.war /usr/local/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh","run"]
