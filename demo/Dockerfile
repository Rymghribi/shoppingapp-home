# stage 1
FROM maven:3-jdk-8-alpine as create_artifact
WORKDIR /usr/src/app
COPY . /usr/src/app
RUN mvn clean install
RUN mvn package

#ENV PORT 5000
#EXPOSE $PORT
#CMD [ "sh", "-c", "mvn -Dserver.port=${PORT} spring-boot:run" ]

# stage 2
FROM openjdk:8-jdk-alpine
WORKDIR /app 
COPY --from=create_artifact /usr/src/app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app/app.jar"]