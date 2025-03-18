**DevSecOps Practices:**

## Introduction

- DevSecOps refers to integrating security practices into the DevOps pipeline, ensuring that security is prioritized throughout the entire software development lifecycle.
- It focuses on automation, continuous monitoring, and proactive risk management while maintaining the speed and agility of DevOps processes.

## Key DevSecOps Practices

### [Credential Scanning](https://microsoft.github.io/code-with-engineering-playbook/CI-CD/dev-sec-ops/secrets-management/credential_scanning/)  (Stage -0)

- - Automatically inspecting a project to ensure that no secrets are included in the project's source code
    - [CodeQL](https://securitylab.github.com/tools/codeql) and [git pre-commit hook](https://pre-commit.com/)

### Static Application Security Testing (SAST)

- - Analyze source code for vulnerabilities before code is deployed.
    - SonarQube, CheckMarx

### Dynamic Application Security Testing (DAST)

- - Test running applications for security vulnerabilities.
    - OWASP ZAP, CodeQL,

### Software Composition Analysis (SCA)

- - Identify known vulnerabilities in open-source libraries and dependencies.
    - Base Image - if your image is built on top of a third-party base image, validate the following:
    - The image comes from a well-known company or open-source group.
    - It is hosted on a reputable registry.
    - The Dockerfile is available, and check for dependencies installed in it.
    - The image is frequently updated - old images might not contain the latest security updates.
    - [Aqua](https://www.aquasec.com/solutions/azure-container-security/),Blackduck

### Continuous Integration / Continuous Deployment (CI/CD) with Security

- - Integrate security checks and tools directly into the CI/CD pipelines (e.g., using Jenkins, GitLab CI).
    - Automate security scans, such as SAST and DAST, to run at different stages of the pipeline (pre-commit, post-commit, pre-deployment).

### Infrastructure as Code (IaC) Security

- - Implement security checks for infrastructure code (e.g., Terraform, CloudFormation) to ensure secure configurations are enforced.
    - Use tools like Checkov, TFLint, or Terrascan to scan IaC files for vulnerabilities before deployment.

### Security Monitoring and Logging

- - Continuously monitor systems for potential threats, using tools like Prometheus, Grafana, Splunk, or ELK stack.
    - Ensure that all logs from applications, infrastructure, and security events are centrally aggregated and analyzed.

### Secrets Management

- - Store and manage secrets (e.g., API keys, database credentials) securely using solutions like Vault (by HashiCorp), AWS Secrets Manager, or Azure Key Vault.
    - Ensure that secrets are injected dynamically into applications at runtime to avoid hardcoding in code.
    - Secret Rotation

### Vulnerability Management

- - Use automated tools (e.g., OWASP Dependency-Check, Snyk) to regularly scan for vulnerabilities in dependencies and third-party libraries.
    - Implement a process to prioritize and fix vulnerabilities as part of the ongoing development workflow.

## Conclusion

- Adopting DevSecOps practices ensures that security is not an afterthought but a core component of the DevOps process. By integrating security tools and practices into the CI/CD pipeline, organizations can ensure secure, agile, and efficient software delivery.
