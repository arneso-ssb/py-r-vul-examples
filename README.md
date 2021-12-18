# py-r-vul-examples
This repo contains Dockerfiles for creating Python- and R-containers with
security vulnerabilities. Used for testing security scanning.

## Build containers
Python:
```
cd python
docker build -t vul-py-test .
```

R:
```
cd R
docker build -t vul-r-test .
```

## Scanning containers
### Docker scan (using Snyk)
```
cd python
docker scan --file Dockerfile vul-py-test --exclude-base
```
Docker scan does not detect issues in the PyPi or R-package.

### Trivy
Trivy is an open source vulnerability scanner:
https://github.com/aquasecurity/trivy
```
trivy --exit-code 1 --light --ignore-unfixed --severity HIGH,CRITICAL vul-py-test
```

Trivy detects issues:
| LIBRARY | VULNERABILITY ID | SEVERITY | INSTALLED VERSION | FIXED VERSION |
|---------|------------------|----------|-------------------|---------------|
| Pillow  | CVE-2021-23437   | HIGH     | 8.3.1             | 8.3.2         |



