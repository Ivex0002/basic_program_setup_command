# basic_program_setup_command

### 버전 확인
- UTF8 : 도커, 깃, vscode, wsl, 파워토이
```powershell
$ids = 'Docker.DockerDesktop','Git.Git','Microsoft.VisualStudioCode','Microsoft.WSL','Microsoft.PowerToys'
$p = '^(?<n>.+?)\s+(?<i>\S+)\s+(?<v>\d[\w.\-+]*)\s+winget$'
$h = @{}
$oldEncoding = [Console]::OutputEncoding
[Console]::OutputEncoding = [System.Text.Encoding]::UTF8
winget list --disable-interactivity | ForEach-Object {
    if ($_ -match $p) {
        $h[$Matches.i] = [pscustomobject]@{
            Name    = $Matches.n.Trim()
            Id      = $Matches.i
            Version = $Matches.v
        }
    }
}
[Console]::OutputEncoding = $oldEncoding
$ids | ForEach-Object {
    if ($h.ContainsKey($_)) { $h[$_] }
    else { [pscustomobject]@{ Name='(not installed)'; Id=$_; Version='-' } }
} | Format-Table Name, Id, Version -AutoSize
```
- 도커, 우분투
```powershell
wsl -l -v
```
### 설치 명령어
- wsl, 도커, 깃, vscode
```powershell
'Microsoft.WSL','Docker.DockerDesktop','Git.Git','Microsoft.VisualStudioCode' | ForEach-Object {
    Write-Host "`n>>> $_" -ForegroundColor Cyan
    winget install --id $_ -e --accept-source-agreements --accept-package-agreements
    Write-Host "exit: $LASTEXITCODE" -ForegroundColor $(if ($LASTEXITCODE -eq 0) { 'Green' } else { 'Red' })
}
```
- 우분투
```powershell
wsl --install -d Ubuntu
```
- 파워토이, 디스코드
```powershell
'Microsoft.PowerToys','Discord.Discord' | ForEach-Object {
    Write-Host "`n>>> $_" -ForegroundColor Cyan
    winget install --id $_ -e --accept-source-agreements --accept-package-agreements
    Write-Host "exit: $LASTEXITCODE" -ForegroundColor $(if ($LASTEXITCODE -eq 0) { 'Green' } else { 'Red' })
}
```
- 도커, 깃, vscode, wsl, 파워토이, 디스코드
```powershell
'Docker.DockerDesktop','Git.Git','Microsoft.VisualStudioCode','Microsoft.WSL','Microsoft.PowerToys','Discord.Discord' | ForEach-Object {
    Write-Host "`n>>> $_" -ForegroundColor Cyan
    winget install --id $_ -e --accept-source-agreements --accept-package-agreements
    Write-Host "exit: $LASTEXITCODE" -ForegroundColor $(if ($LASTEXITCODE -eq 0) { 'Green' } else { 'Red' })
}
```
