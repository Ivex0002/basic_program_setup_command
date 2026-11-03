# basic_program_setup_command

### 버전 확인
```
$ids = 'Docker.DockerDesktop','Git.Git','Microsoft.VisualStudioCode'
$p = '^(?<n>.+?)\s+(?<i>\S+)\s+(?<v>\d[\w.\-+]*)\s+winget$'
$h = @{}
winget list --disable-interactivity | ForEach-Object { if ($_ -match $p) { $h[$Matches.i] = [pscustomobject]@{ Name=$Matches.n.Trim(); Id=$Matches.i; Version=$Matches.v } } }
$ids | ForEach-Object { if ($h.ContainsKey($_)) { $h[$_] } else { [pscustomobject]@{ Name='(not installed)'; Id=$_; Version='-' } } } | Format-Table Name, Id, Version -AutoSize
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
