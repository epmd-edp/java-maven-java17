# Java Maven Spring Boot Demo

A production-ready Spring Boot application demonstrating best practices for containerized Java applications with comprehensive test coverage.

## Technology Stack

- Java 17 - LTS version with modern language features
- Spring Boot 3.5.6 - Latest Spring Boot framework
- Maven 3 - Dependency management and build automation
- JUnit 5 - Modern testing framework
- JaCoCo 0.8.12 - Code coverage analysis with 80% minimum threshold
- Docker - Alpine-based containerization with optimized JRE image

## Architecture Approach

### Containerization

- Multi-stage Docker build with Eclipse Temurin JRE 17
- Security hardened - runs as non-root user (`nobody:nogroup`)
- Optimized startup - uses `exec` for proper signal handling (PID 1)
- Runtime configuration - JVM options via `$JAVA_OPTS` environment variable

### Testing Strategy

- Unit tests with `@WebMvcTest` for controller layer
- Integration tests with `@SpringBootTest` for application context
- Coverage enforcement - JaCoCo checks minimum 80% code coverage
- Excludes - Application main class excluded from coverage metrics

### Code Quality

- Automated test execution during Maven build lifecycle
- Coverage reports - HTML, XML, and CSV formats
- CI/CD ready - Fail-fast on coverage violations

## Quick Start

### Build and Run

```bash
# Build the application
./mvnw clean package

# Run tests with coverage
./mvnw clean test

# Run with coverage check
./mvnw verify

# Run the application
java -jar target/java-maven-springboot-0.0.1-SNAPSHOT.jar
```

### Docker

```bash
# Build image
docker build -t java-maven-springboot:latest .

# Run container
docker run -p 8080:8080 \
  -e JAVA_OPTS="-Xmx512m -Xms256m" \
  java-maven-springboot:latest
```

### API Endpoints

- `GET /api/hello` - Returns greeting message

## Test Coverage

View coverage reports after running tests:

```bash
open target/site/jacoco/index.html
```

Current coverage: 100% of application code

## Learn More

This demo is part of the [KubeRocketCI](https://docs.kuberocketci.io) platform, which provides a complete CI/CD solution for Kubernetes-native applications.

For comprehensive guides on building cloud-native applications with KubeRocketCI, visit the [official documentation](https://docs.kuberocketci.io).

## License

Apache License 2.0
