# This is a multi-stage Dockerfile for building and running the vprofile application using Tomcat and Java 21.

# Here we are using this baseimage to build the artifact
FROM maven:3.9.9-eclipse-temurin-21-jammy AS BUILD_IMAGE   

# In this step we are cloning the repository
RUN git clone https://github.com/nsanjula/vprofile-project.git

# Here we are running multiple commands to build the artifact
# The best practice is to execute multiple commands in a single RUN statement to reduce the number of layers in the Docker image, which can help optimize the build process and reduce the final image size.
RUN cd vprofile-project && git checkout containers && mvn install

# Next we are using the tomcat base image to run the artifact
FROM tomcat:10-jdk21
LABEL "Project"="vprofile"
LABEL "Author"="Nisal"

# In this step we are removing default files in the webapp directory
RUN rm -rf /usr/local/tomcat/webapps/*

# Next we are copying the built artifact from the build stage to the tomcat webapps directory. We are also renaming the artifact to ROOT.war so that it can be accessed directly without specifying the context path.
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

# Next we expose the default Tomcat port 8080 and specify the command to run the Tomcat server when the container starts.
EXPOSE 8080
CMD [ "catalina.sh", "run" ]