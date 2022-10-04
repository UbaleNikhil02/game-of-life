FROM tomcat:9

RUN rm -rf /usr/local/tomcat/webapps/*

COPY target/gameoflife.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 9090
CMD ["catalina.sh", "run"] 
