# Stage 1: Build with Maven + JDK
FROM maven:3.9.3-eclipse-temurin-17 AS builder

WORKDIR /opt/app

# Copy source code
COPY . .

# Build the JAR
RUN mvn clean package -DskipTests

# Stage 2: Run the JAR with minimal JRE
FROM eclipse-temurin:17-jre-alpine

WORKDIR /opt/app

# Copy the JAR from builder stage
COPY --from=builder /opt/app/target/*.jar app.jar

# Run the app
ENTRYPOINT ["java", "-jar", "app.jar"]
