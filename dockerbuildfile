
FROM gcr.io/distroless/java  
COPY  target/test-0.0.1-SNAPSHOT.jar test-0.0.1-SNAPSHOT.jar  
EXPOSE 8082  
ENTRYPOINT ["java","-jar","/test-0.0.1-SNAPSHOT.jar"]  
