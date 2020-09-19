# httpcheck
Take a list of domains and probe for working HTTP and HTTPS servers





## Install
```
wget <master> -O /usr/local/bin/httpcheck
```

## Basic Usage
```
httpcheck < domains.txt

# or

cat domains.txt | httpcheck
```

Inspired by [tomnomnom's httprobe](https://github.com/tomnomnom/httprobe) but this is written using just POSIX and curl instead of GO.
