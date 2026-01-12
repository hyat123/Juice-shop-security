# CI/CD Security Pipeline – OWASP Juice Shop

This repository demonstrates an automated CI/CD security pipeline using GitHub Actions.
The pipeline integrates multiple security tools to scan an intentionally vulnerable
application (OWASP Juice Shop) before and after deployment.

## Pipeline Overview

The workflow runs sequential security checks within a single CI job using an ephemeral
deployment environment.

### Pre-Deployment Security Scanning
- **Trivy filesystem scan** – identifies vulnerable dependencies and insecure files.
- **Trivy container image scan** – detects known CVEs in the Juice Shop Docker image.

### Deployment
- OWASP Juice Shop is deployed as a Docker container on the CI runner.
- The environment exists only for the duration of the pipeline run.

### Post-Deployment Security Scanning
- **OWASP ZAP baseline scan** – performs dynamic application-layer security testing.
- **Nmap vulnerability scan** – identifies exposed services and common network issues.

## Security Reports (Artifacts)

Each pipeline execution produces downloadable artifacts:
- `trivy_fs_scan.txt`
- `trivy_image_scan.txt`
- `zap_report.html`
- `nmap_vuln_scan.txt`

These reports provide evidence of detected security warnings and misconfigurations.

## Tools Used
- GitHub Actions
- Docker
- OWASP Juice Shop
- Trivy
- OWASP ZAP
- Nmap

## Purpose
This project illustrates how security controls can be embedded into a CI/CD pipeline
using automated, repeatable scanning stages. It reflects common DevSecOps practices
used to identify security issues early and during runtime.

> OWASP Juice Shop is intentionally vulnerable and used for educational purposes only.
