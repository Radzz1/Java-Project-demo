# ---------- Stage 1: Build ----------
FROM maven:3.9.9-eclipse-temurin-17 AS builder

WORKDIR /app

# Copy project files
COPY . .

# Build the project
RUN mvn clean package -DskipTests

# ---------- Stage 2: Run ----------
FROM openjdk:17-jdk-slim

WORKDIR /app

# Copy JAR from builder stage
COPY --from=builder /app/target/sample.jar app.jar

# Run the app
ENTRYPOINT ["java", "-jar", "app.jar"]
