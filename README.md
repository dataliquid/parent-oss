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

## Projects Using This Parent

- [distribution-verifier-maven-plugin](distribution-verifier-maven-plugin/): Maven plugin for verifying distribution archives
- [json-yaml-validator-maven-plugin](json-yaml-validator-maven-plugin/): Maven plugin for validating JSON and YAML files against schemas

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the Apache License 2.0 - see the LICENSE file for details.