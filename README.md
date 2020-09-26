# httpcheck
Take a list of domains and probe for working HTTP and HTTPS servers  
Depends on `xargs`, `curl`, `sh`  

## Quick: just create an alias
It's just a wrapper around curl with xargs for parallization.   
You can just create your own alias in the shell and call it like so:
```
alias httpcheck="xargs -n1 -P5 curl --connect-timeout 3 -sLI -o /dev/null --write-out '%{http_code}\t%{url_effective}\n' < /dev/stdin"

cat targets.txt | httpcheck
```
I recommend splitting large lists into chunks

## Install
### download the script to $PATH
```
wget https://raw.githubusercontent.com/jsav0/httpcheck/master/httpcheck -O /usr/local/bin/httpcheck
chmod +x /usr/local/bin/httpcheck
```

## Basic Usage
Simple usage:  
```
httpcheck < domains.txt
```
```
cat targets.txt | httpcheck
```
Pipe from other commands:  
```
$ subfinder -d yahoo.com -silent | head -n20 | httpcheck -v
http://66.218.84.137
http://74.6.136.150
http://98.137.11.143
https://ds-global3.l7.search.ystg1.b.yahoo.com
http://src.g03.yahoodns.net
```

## Verbose
By default, the script outputs just the domains that return a status code 200. It will follow 301s attempting to get there.   
If you would like more verbose output, ie., if you want to see the final status codes being returned, pass the `-v` flag. 

### Example Output
```
$ cat targets.txt | httpcheck -v
200     http://66.218.84.137
200     http://74.6.136.150
200     http://98.137.11.143
200     https://ds-global3.l7.search.ystg1.b.yahoo.com
200     http://src.g03.yahoodns.net
```

Similar to [tomnomnom's httprobe](https://github.com/tomnomnom/httprobe) but this is written using just POSIX and curl instead of GO.
