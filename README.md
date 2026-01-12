# DevSecOps CI/CD Security Pipeline (OWASP Juice Shop)

This project demonstrates a multi-layer DevSecOps CI/CD security pipeline using GitHub Actions.  
It deploys OWASP Juice Shop in an ephemeral CI environment and runs automated security scans pre- and post-deployment.

## What this pipeline does

### Pre-deployment (Shift Left)
- **Trivy filesystem scan**: scans the repository for vulnerable dependencies and issues.
- **Trivy image scan**: scans the OWASP Juice Shop container image for CVEs.

### Deployment (Ephemeral Environment)
- Starts **OWASP Juice Shop** as a Docker container on the GitHub Actions runner.

### Post-deployment (Runtime / DAST + Network)
- **OWASP ZAP baseline scan**: application-layer dynamic security testing (safe baseline mode).
- **Nmap scan**: network/service exposure and vulnerability scripting.

## Outputs (Artifacts)
Each workflow run uploads reports as GitHub Actions artifacts:
- `trivy_fs_scan.txt`
- `trivy_image_scan.txt`
- `zap_report.html`
- `nmap_vuln_scan.txt`

## Tech Stack
- GitHub Actions
- Docker
- OWASP Juice Shop
- Trivy
- OWASP ZAP (containerised baseline scan)
- Nmap

## How to run locally (optional)
1. Start Juice Shop:
   ```bash
   docker run -d -p 3000:3000 bkimminich/juice-shop
