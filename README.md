# PS_GitBash_PromptFiles

## PowerShell Prompt
* Open Powershell
* notepad $PROFILE
* NB: If $PROFILE path does not exist, run ```New-Item -ItemType File -Path $PROFILE -Force``` from PowerShell
* Copy Paste the below function 'prompt'

```powershell
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

---

## GitBash Prompt (Windows)
* Open Git Bash
* mkdir ~/.config
* mkdir ~/.config/git
* touch git-prompt.sh
* notepad ~/.config/git/git-prompt.sh
* Copy Paste the below content for $PS1

```bash
PS1='\[\033]0;GitBash: $PWD\007\]' # set window title
PS1="$PS1"'\n'			# new line
PS1="$PS1"'\[\033[37m\]'	# change to light gray
PS1="$PS1"'['			# [
PS1="$PS1"'\[\033[92m\]'	# change to light green
PS1="$PS1"'\u'			# user
PS1="$PS1"'\[\033[95m\]'	# change to light magenta
PS1="$PS1"'@'			# @
PS1="$PS1"'\[\033[92m\]'	# change to light green
PS1="$PS1"'\h'			# host
PS1="$PS1"'\[\033[37m\]'	# change to light gray
PS1="$PS1"'] in ['		# ] in [
PS1="$PS1"'\[\033[93m\]'	# change to light yellow
PS1="$PS1"'\w'			# current working directory
PS1="$PS1"'\[\033[37m\]'	# change to light gray
PS1="$PS1"']'			# ]
if test -z "$WINELOADERNOEXEC"
then
	GIT_EXEC_PATH="$(git --exec-path 2>/dev/null)"
	COMPLETION_PATH="${GIT_EXEC_PATH%/libexec/git-core}"
	COMPLETION_PATH="${COMPLETION_PATH%/lib/git-core}"
	COMPLETION_PATH="$COMPLETION_PATH/share/git/completion"
	if test -f "$COMPLETION_PATH/git-prompt.sh"
	then
		. "$COMPLETION_PATH/git-completion.bash"
		. "$COMPLETION_PATH/git-prompt.sh"
		PS1="$PS1"'\[\033[96m\]'	# change to light cyan
		PS1="$PS1"'`__git_ps1`'		# bash function
	fi
fi
PS1="$PS1"'\[\033[0m\]'		# change color
PS1="$PS1"'\n'			# new line
PS1="$PS1"'$ '  		# $
```

---

## Bash Prompt (Linux)
* Open ~/.bashrc
* Copy the following to end of file

```bash
# Color codes
cRESET="\[\e[m\]"
cBLACK="\[\e[30m\]"
cRED="\[\e[31m\]"
cGREEN="\[\e[32m\]"
cYELLOW="\[\e[33m\]"
cBLUE="\[\e[34m\]"
cPINK="\[\e[35m\]"
cCYAN="\[\e[36m\]"
cWHITE="\[\e[37m\]"

# Elements Naming
eNEWLINE="\n"
eUSERNAME="\u"
eFOLDERPATH="\w"
eFOLDERNAME="\W"

# Build PS1
PS1=$eNEWLINE
PS1+="["
PS1+=$cGREEN
PS1+=$eUSERNAME
PS1+=$cRESET
PS1+="] in ["
PS1+=$cYELLOW
PS1+=$eFOLDERPATH
PS1+=$cRESET
PS1+="]"
PS1+=$eNEWLINE
PS1+="$ "

export PS1
```
