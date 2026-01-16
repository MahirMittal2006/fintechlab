# FinTech Lab 1 & 2 — Spring Boot REST API + GitHub + Azure Deployment

## Overview

This repository contains the work completed in FinTech Lab 1 and Lab 2. It covers:

- Installing and verifying development tools
- Understanding REST API basics
- Creating a Spring Boot REST API using Spring Initializr
- Running the backend locally
- Initializing Git and pushing to GitHub
- Deploying the Spring Boot application to Microsoft Azure

## Software Requirements

Required tools:

- Node.js
- Angular
- VS Code
- Eclipse
- MySQL
- Postman
- Git
- NVM

## Installation Verification Commands

Run these in a terminal to confirm installations:

```bash
node -v
npm -v
nvm --version
ng version
code --version
mysql --version
git --version
```

## REST API (Short Notes)

A REST API (Representational State Transfer) enables clients (frontend/mobile) to communicate with a backend using HTTP methods.

Key concepts:

- Resources: users, products, orders
- Endpoints (URLs) identify resources
- HTTP Methods (CRUD): GET (read), POST (create), PUT (update), DELETE (delete)
- Stateless: each request contains all required information

## Maven & Eclipse Setup

1. Open Eclipse
2. Help → Eclipse Marketplace
3. Search `Maven` and install "Maven Integration for Eclipse"
4. After install: Window → Preferences and verify Maven is present

## Spring Boot Project Setup (Spring Initializer)

We used Spring Initializer (https://start.spring.io/) with the following:

- Project: Maven
- Language: Java
- Spring Boot: latest stable
- Packaging: Jar
- Java: 11 or 17 (recommended: 17)
- Dependency: Spring Web

## Import Project into Eclipse

File → Import → Existing Maven Projects → Select project folder

Wait for Maven to finish building project.

## Run the Application

Click the Run button in Eclipse and open:

http://localhost:8080/

If you see the Whitelabel Error Page, the app is running but no endpoint is defined yet.

## Example REST Controller

Create a Java file in `com.example.demo` (e.g., `Hello.java`):

```java
package com.example.demo;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class Hello {

    @GetMapping("/")
    public String index() {
        return "Greetings from MIT-FIS!";
    }
}
```

Opening `http://localhost:8080/` should display: "Greetings from MIT-FIS!"

## Spring Boot Annotations Used

- `@SpringBootApplication`: main entry point, enables auto-configuration and component scanning
- `@RestController`: declares a RESTful controller class
- `@GetMapping`: maps HTTP GET requests to a method

## Git & GitHub Commands (Push Project)

```bash
git init
git add .
git commit -m "Initial FinTech Lab project"
git remote add origin <repository_url>
git branch -M main
git push origin main
```

## Deploying to Azure (High-level Steps)

1. Open Azure Cloud Shell: https://shell.azure.com
2. Clone your GitHub repo:

```bash
git clone <your-repository-url> my-webapp
cd my-webapp
```

3. Configure Azure Web App plugin for Maven:

```bash
mvn com.microsoft.azure:azure-webapp-maven-plugin:2.13.0:config
```

When prompted, example choices used in the lab:

- Create new run configuration: Y
- OS: Linux
- Java Version: Java 17
- Pricing Tier: P1v2 (or F1 for free)
- Region: centralindia

This generates Azure configuration values such as `appName` and `resourceGroup` in `pom.xml` (azure plugin section).

4. Build and deploy:

```bash
mvn clean package
mvn azure-webapp:deploy
```

After deployment Azure will provide a web app URL to access the running Spring Boot app.

## Conclusion

This repository documents a complete workflow for:

- Creating a Spring Boot REST API
- Running and testing locally
- Pushing the project to GitHub
- Deploying the Spring Boot app to Microsoft Azure

