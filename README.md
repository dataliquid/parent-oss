# Parent OSS

[![CI](https://github.com/dataliquid/parent-oss/actions/workflows/ci.yml/badge.svg)](https://github.com/dataliquid/parent-oss/actions/workflows/ci.yml)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.dataliquid/parent-oss/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.dataliquid/parent-oss)

Parent POM for open source projects.

## Overview

This project provides a parent POM configuration for open source Maven projects. It includes common configurations, plugin management, and dependency management to standardize build processes across multiple projects.

## Usage

To use this parent POM in your project, add the following to your `pom.xml`:

```xml
<parent>
    <groupId>com.dataliquid</groupId>
    <artifactId>parent-oss</artifactId>
    <version>2.1.0</version>
</parent>
```

## Features

- Standardized plugin configurations
- Common dependency management
- Build optimization settings
- Release management configuration
- Quality assurance tools integration
- Automatic code formatting with CI-aware profiles

## Code Formatting

This parent POM provides automatic code formatting using the `formatter-maven-plugin` with CI-aware profile activation.

### Automatic Profile Activation

The formatter profiles activate automatically based on the CI environment:

- **Local Development** (CI environment variable not set):
  - Profile `format-code` activates automatically
  - Runs `formatter:format` during the validate phase
  - Automatically formats code according to the configured style guide

- **CI/CD Pipeline** (CI=true):
  - Profile `format-code-validation` activates automatically
  - Runs `formatter:validate` during the validate phase
  - Fails the build if code is not properly formatted

### Default Configuration

The parent POM includes:
- **Dependency**: `com.dataliquid.guidelines:coding-conventions` containing formatter styles
- **Default Styles**: 
  - Java: `codestyles/default/java-formatter.xml`
  - JavaScript: `codestyles/default/javascript-formatter.xml`
  - JSON: `codestyles/default/json-formatter.properties`
  - HTML: `codestyles/default/html-formatter.properties`
  - CSS: `codestyles/default/css-formatter.properties`
- **Line Ending**: LF (Unix-style)
- **Encoding**: UTF-8

### Overriding Formatter Configuration

Child projects can override the formatter configuration while still using the styles from the parent's dependency:

```xml
<build>
    <plugins>
        <plugin>
            <groupId>net.revelc.code.formatter</groupId>
            <artifactId>formatter-maven-plugin</artifactId>
            <configuration>
                <!-- Use alternative style from the classpath dependency -->
                <configFile>codestyles/traditional/eclipse-codestyle.xml</configFile>
            </configuration>
        </plugin>
    </plugins>
</build>
```

All styles are loaded from the classpath, so no local files are needed in your project.

### Disabling Formatter

To skip formatting completely, deactivate both profiles:

```bash
mvn clean validate -P!format-code,!format-code-validation
```

## Projects Using This Parent

- [distribution-verifier-maven-plugin](distribution-verifier-maven-plugin/): Maven plugin for verifying distribution archives
- [json-yaml-validator-maven-plugin](json-yaml-validator-maven-plugin/): Maven plugin for validating JSON and YAML files against schemas

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the Apache License 2.0 - see the LICENSE file for details.