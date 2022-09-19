FROM tomcat:9

WORKDIR /mnt

RUN rm -rf /usr/local/tomcat/webapps/*

COPY target/gameoflife.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8090
CMD ["catalina.sh", "run"] 
