# httpcheck
Take a list of domains and probe for working HTTP and HTTPS servers

## Install
### download the shell script to $PATH
```
wget https://raw.githubusercontent.com/jsav0/httpcheck/master/httpcheck -O /usr/local/bin/httpcheck
chmod +x /usr/local/bin/httpcheck
```

## Basic Usage
```
httpcheck < domains.txt

# or

cat domains.txt | httpcheck
```

## Verbose
By default, the script outputs just the domains that return a status code 200. It will follow 301s to get there.   
If you would like more verbose output, ie., if you want to see the status codes being returned by curl, pass the `-v` flag. 
```
cat targets.txt | httpcheck -v
```

## Example Output
```
$ cat targets.txt | httpcheck
66.218.84.137
74.6.136.150
98.137.11.143
ds-global3.l7.search.ystg1.b.yahoo.com
src.g03.yahoodns.net
```

```
$ cat targets.txt | httpcheck -v
200     66.218.84.137
200     74.6.136.150
200     98.137.11.143
200     ds-global3.l7.search.ystg1.b.yahoo.com
200     src.g03.yahoodns.net
```

Similar to [tomnomnom's httprobe](https://github.com/tomnomnom/httprobe) but this is written using just POSIX and curl instead of GO.
