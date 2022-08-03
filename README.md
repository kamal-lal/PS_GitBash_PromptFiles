# PS_GitBash_PromptFiles

## PowerShell Prompt
* Open Powershell
* notepad $PROFILE
* Copy Paste the function 'prompt'

```
function prompt
{
    Write-Host ""
    Write-Host -NoNewLine -ForegroundColor DarkGray "[" 
    Write-Host -NoNewLine -ForegroundColor DarkGreen ([System.Environment]::UserName) 
    Write-Host -NoNewLine -ForegroundColor DarkGray "@" 
    Write-Host -NoNewLine -ForegroundColor DarkGreen ([net.dns]::GetHostName())
    Write-Host -NoNewLine -ForegroundColor DarkGray "] in [" 
    Write-Host -NoNewLine -ForegroundColor DarkCyan "$pwd" 
    Write-Host -ForegroundColor DarkGray "]" 
    
    [Console]::ResetColor()
    
    return "> " 
}
```

## GitBash Prompt
* Open Git Bash
* mkdir ~/.config
* mkdir ~/.config/git
* touch git-prompt.sh
* notepad ~/.config/git/git-prompt.sh
* Copy Paste the content for updating $PS1
