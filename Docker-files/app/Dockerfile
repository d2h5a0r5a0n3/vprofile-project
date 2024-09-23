FROM openjdk:11 AS BUILD_IMG
RUN sudo apt update && apt install maven -y
RUN git clone https://github.com/d2h5a0r5a0n3/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:9-jre11
LABEL "project"="vprofile"
LABEL "Author"="d2h5a0r5a0n3"
RUN rm /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMG vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD [ "catalina.sh","run" ]