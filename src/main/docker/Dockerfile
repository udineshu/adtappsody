# Sample Dockerfile for use with the Docker file mode
FROM openjdk:8-jdk-alpine
LABEL PROJECT_NAME=order \
      PROJECT=order
# In maven/ the files as specified in the <assembly> section is stored
# and need to be added manually
ADD maven/  / 
RUN echo 'Jar name is' $JAR_FILE \n
COPY maven/order-0.0.1-SNAPSHOT.jar  app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/app.jar"]

