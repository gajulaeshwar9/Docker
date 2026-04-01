FROM maven:3.9.9-eclipse-temurin-21-jammy AS BUILDER
RUN git clone https://github.com/hkhcoder/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn install 

FROM tomcat:10-jdk21
LABEL "Project"="Vprofile"
LABEL "Author"="Eshwar"
RUN rm -rf /usr/local/webapps/*
COPY --from=BUILDER vprofile-project/target/vprofile-v2.war /usr/local/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
