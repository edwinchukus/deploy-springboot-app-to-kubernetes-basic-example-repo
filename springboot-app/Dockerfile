FROM maven:3.6.3-ibmjava-8-alpine AS build
LABEL description="This is Image to build spring boot REST API for Delta State electoral Services"
COPY election-register-service/src /home/app/src
COPY election-register-service/pom.xml /home/app
RUN mvn -f /home/app/pom.xml package -Dmaven.test.skip=true


FROM openjdk:8u171-jdk-alpine3.7
LABEL description="This is Image to build spring boot REST API for Delta State electoral Services"
WORKDIR /usr/src/app
COPY --from=build /home/app/target/election-register-service.jar /usr/src/app/election-register-service.jar
EXPOSE 8081
ENTRYPOINT ["java", "-jar", "/usr/src/app/election-register-service.jar","-Dspring.data.mongodb.uri=mongodb://mongodb:27017/deltaStateGovtNg?ssl=false" ]
