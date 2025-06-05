# Stage 1: Build the application
FROM maven:3.9.9 AS builder

WORKDIR /app
RUN git clone --depth=1 --branch containers https://github.com/hkhcoder/vprofile-project.git .
RUN mvn clean install -DskipTests

# Stage 2: Run the application
FROM tomcat:10-jdk21

# Clean default webapps
RUN rm -rf /usr/local/tomcat/webapps/*

# Copy WAR file from the builder stage
COPY --from=builder /app/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080

CMD ["catalina.sh", "run"]
