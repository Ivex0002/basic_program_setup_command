# basic_program_setup_command

### 버전 확인
```
winget list --id Docker.DockerDesktop -e; `
winget list --id Git.Git -e; `
winget list --id Microsoft.VisualStudioCode -e
```
### 설치 명령어
```
winget install --id Docker.DockerDesktop -e --accept-source-agreements --accept-package-agreements; winget install --id Git.Git -e --accept-source-agreements --accept-package-agreements; winget install --id Microsoft.VisualStudioCode -e --accept-source-agreements --accept-package-agreements
```
```power shell
winget install --id Docker.DockerDesktop -e `
  --accept-source-agreements `
  --accept-package-agreements

winget install --id Git.Git -e `
  --accept-source-agreements `
  --accept-package-agreements

winget install --id Microsoft.VisualStudioCode -e `
  --accept-source-agreements `
  --accept-package-agreements
```
