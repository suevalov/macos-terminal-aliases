### MacOS Terminal Aliases ###

A list of useful terminal aliases and utils.

Feel free to contribute.

#### Navigation ####
```bash
alias cd..='cd ..'
alias ..='cd ..'
alias ...='cd ../..'
alias ....='cd ../../..'
alias .....='cd ../../../..'
alias ll='ls -alF'
```

#### Browsers ####
```bash

alias safari="open -a safari"
alias firefox="open -a firefox"
alias opera="open -a opera"
alias chrome="open -a google\ chrome"
alias canary="open -a google\ chrome\ canary"

# Launch installed browsers for a specific URL
# Usage: browsers "http://www.google.com"
function browsers(){
	chrome $1
	opera $1
	firefox $1
	safari $1
}

```

#### Git ####
```bash
alias g='git'
alias gst='git status'
alias gco='git checkout'
alias gcob='git checkout -b'
alias gcm='git commit -m'
alias gamend='git commit -a --amend'
alias gdeletemerged='git branch --merged | egrep -v "(^\*|master|dev)" | xargs git branch -d'
```

#### Server ####
```bash

# Start an HTTP server from a directory, optionally specifying the port
function server() {
	local port="${1:-8000}"
	open "http://localhost:${port}/"
	# Set the default Content-Type to `text/plain` instead of `application/octet-stream`
	# And serve everything as UTF-8 (although not technically correct, this doesn’t break anything for binary files)
	python -c $'import SimpleHTTPServer;\nmap = SimpleHTTPServer.SimpleHTTPRequestHandler.extensions_map;\nmap[""] = "text/plain";\nfor key, value in map.items():\n\tmap[key] = value + ";charset=UTF-8";\nSimpleHTTPServer.test();' "$port"
}

```

#### Java ####
```bash

# Java Version Changer - now updated for JDK 9
alias java_ls='/usr/libexec/java_home -V 2>&1 | grep -E "(jdk\d\.\d\.\d|jdk-\d\.)" | cut -d , -f 1 | colrm 1 4 | grep -v Home'

function java_use() {
    export JAVA_HOME=$(/usr/libexec/java_home -v $1)
    export PATH=$JAVA_HOME/bin:$PATH
    java -version
}

```

#### Other ####
```bash

alias please='sudo'
alias lsd='ls -l | grep "^d"'
alias f='open -a Finder'

# Empty trash
alias emptytrash='sudo rm -rfv /Volumes/*/.Trashes; rm -rfv ~/.Trash'

# Hide/show all desktop icons (useful when presenting)
alias hidedesktop='defaults write com.apple.finder CreateDesktop -bool false && killall Finder'
alias showdesktop='defaults write com.apple.finder CreateDesktop -bool true && killall Finder'

# File size
alias filesize="stat -f \"%z bytes\""

# Show path
alias path='echo -e ${PATH//:/\\n}'

# Copy w/ progress
cp_p () {
  rsync -WavP --human-readable --progress $1 $2
}

```

#### BrowserStack ####
```bash

function openurl(){
	if [ $2 ]
	then
	  url=$1"&host_ports=$2"
	fi
	open -a google\ chrome ${url}
}

function androidnexus(){
	local url="http://www.browserstack.com/start#os=android&os_version=4.0.3&device=Samsung+Galaxy+Nexus&zoom_to_fit=true&url=$1&start=true"
	openurl $url $2
}

function ipad3(){
	local url="http://www.browserstack.com/start#os=ios&os_version=5.1&device=iPad+3rd&zoom_to_fit=true&resolution=1024x768&speed=1&url=$1&start=true"
	openurl $url $2
}

function ipad3ios6(){
	local url="http://www.browserstack.com/start#os=ios&os_version=6.1&device=iPad+3rd&zoom_to_fit=true&resolution=1024x768&speed=1&url=$1&start=true"
	openurl $url $2
}

function ipad2(){
	local url="http://www.browserstack.com/start#os=ios&os_version=5.1&device=iPad+2nd&zoom_to_fit=true&resolution=1024x768&speed=1&url=$1&start=true"
	openurl $url $2
}

function win7ie8(){
	local url="http://www.browserstack.com/start#os=Windows&os_version=7&browser=IE&browser_version=8.0&zoom_to_fit=true&resolution=1024x768&speed=1&url=$1&start=true"
	openurl $url $2
}

function win7ie9(){
	local url="http://www.browserstack.com/start#os=Windows&os_version=7&browser=IE&browser_version=9.0&zoom_to_fit=true&resolution=1024x768&speed=1&url=$1&start=true"
	openurl $url $2
}

function win8ie10(){
	local url="http://www.browserstack.com/start#os=Windows&os_version=8&browser=IE&browser_version=10.0&zoom_to_fit=true&resolution=1024x768&speed=1&url=$1&start=true"
	openurl $url $2
}

function winxpie8(){
	local url="http://www.browserstack.com/start#os=Windows&os_version=XP&browser=IE&browser_version=8.0&zoom_to_fit=true&resolution=1024x768&speed=1&url=$1&start=true"
	openurl $url $2
}

function winxpie7(){
	local url="http://www.browserstack.com/start#os=Windows&os_version=XP&browser=IE&browser_version=7.0&zoom_to_fit=true&resolution=1024x768&speed=1&url=$1&start=true"
	openurl $url $2
}

function winxpie6(){
	local url="http://www.browserstack.com/start#os=Windows&os_version=XP&browser=IE&browser_version=6.0&zoom_to_fit=true&resolution=1024x768&speed=1&url=$1&start=true"
	openurl $url $2
}

function win7chrome(){
	local url="http://www.browserstack.com/start#os=Windows&os_version=7&browser=Chrome&browser_version=21.0&zoom_to_fit=true&resolution=1024x768&speed=1&url=$1&start=true"
	openurl $url $2
}

function win7ff(){
	local url="http://www.browserstack.com/start#os=Windows&os_version=7&browser=Firefox&browser_version=16.0&zoom_to_fit=true&resolution=1024x768&speed=1&url=$1&start=true"
	openurl $url $2
}

```
