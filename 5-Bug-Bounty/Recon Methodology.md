
### **1. [Builtwith](https://builtwith.com/example.com)**

### **2. wappalyzer extension**

### **3. curl**

```
curl -skIL https://example.com
```
### **4. [Securityheaders](https://securityheaders.com/?q=example.com&followRedirects=on)**

### **5. Nmap**

```
nmap -p80,443 -A example.com
```

```
nmap -p80,443 --script=http-server-header example.com
```

```
nmap example.com
```

### **6. Naabu**

```
sudo naabu -host https://example.com
```

### **7. ffuf**

```
ffuf -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -u https://example.com/FUZZ
```

### **8. dirb**

```
dirb https://example.com
```

### **9. dirbuster**

```
dirbuster
```


### **10. gobuster**

# Gobuster CheatSheet[¶](https://3os.org/penetration-testing/cheatsheets/gobuster-cheatsheet/#gobuster-cheatsheet "Permanent link")

## Common Gobuster Commands[¶](https://3os.org/penetration-testing/cheatsheets/gobuster-cheatsheet/#common-gobuster-commands "Permanent link")

### dir Mode[¶](https://3os.org/penetration-testing/cheatsheets/gobuster-cheatsheet/#dir-mode "Permanent link")

`gobuster dir -u https://example.com -w ~/wordlists/shortlist.txt`

With content length

Web application security tools

`gobuster dir -u https://example.com -w ~/wordlists/shortlist.txt -l`

### dns Mode[¶](https://3os.org/penetration-testing/cheatsheets/gobuster-cheatsheet/#dns-mode "Permanent link")

`gobuster dns -d example.com -t 50 -w common-names.txt`

`gobuster dns -d example.com-w ~/wordlists/subdomains.txt`

With Show IP

`gobuster dns -d example.com -w ~/wordlists/subdomains.txt -i`

Base domain validation warning when the base domain fails to resolve

`gobuster dns -d example.com -w ~/wordlists/subdomains.txt -i`

Wildcard DNS is also detected properly:

`gobuster dns -d 0.0.1.xip.io -w ~/wordlists/subdomains.txt`

### vhost Mode[¶](https://3os.org/penetration-testing/cheatsheets/gobuster-cheatsheet/#vhost-mode "Permanent link")

`gobuster vhost -u https://example.com -w common-vhosts.txt`

s3 Mode

`gobuster s3 -w bucket-names.txt`

## Available Modes[¶](https://3os.org/penetration-testing/cheatsheets/gobuster-cheatsheet/#available-modes "Permanent link")

|Switch|Description|
|---|---|
|dir|the classic directory brute-forcing mode|
|dns|DNS subdomain brute-forcing mode|
|s3|Enumerate open S3 buckets and look for existence and bucket listings|
|vhost|irtual host brute-forcing mode (not the same as DNS!)|

## Global Flags[¶](https://3os.org/penetration-testing/cheatsheets/gobuster-cheatsheet/#global-flags "Permanent link")

|Short Switch|Long Switch|Description|
|---|---|---|
|-z|--no-progress|Don't display progress|
|-o|--output string|Output file to write results to (defaults to stdout)|
|-q|--quiet|Don't print the banner and other noise|
|-t|--threads int|Number of concurrent threads (default 10)|
|-i|--show-ips|Show IP addresses|
||--delay duration|DNS resolver timeout (default 1s)|
|-v,|--verbose|Verbose output (errors)|
|-w|--wordlist string|Path to the wordlist|

## DNS Mode Options[¶](https://3os.org/penetration-testing/cheatsheets/gobuster-cheatsheet/#dns-mode-options "Permanent link")

|Short Switch|Long Switch|Description|
|---|---|---|
|-h,|--help|help for dns|
|-d,|--domain string|The target domain|
|-r,|--resolver string|Use custom DNS server (format server.com or server.com:port)|
|-c,|--show-cname|Show CNAME records (cannot be used with '-i' option)|
|-i,|--show-ips|Show IP addresses|
||--timeout duration|DNS resolver timeout (default 1s)|

## DIR Mode Options[¶](https://3os.org/penetration-testing/cheatsheets/gobuster-cheatsheet/#dir-mode-options "Permanent link")

|Short Switch|Long Switch|Description|
|---|---|---|
|-h,|--help|help for dir|
|-f,|--add-slash|Append / to each request|
|-c,|--cookies string|Cookies to use for the requests|
|-e,|--expanded|Expanded mode, print full URLs|
|-x,|--extensions string|File extension(s) to search for|
|-r,|--follow-redirect|Follow redirects|
|-H,|--headers stringArray|Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2'|
|-l,|--include-length|Include the length of the body in the output|
|-k,|--no-tls-validation|Skip TLS certificate verification|
|-n,|--no-status|Don't print status codes|
|-P,|--password string|Password for Basic Auth|
|-p,|--proxy string|Proxy to use for requests [http(s)://host:port]|
|-s,|--status-codes string|Positive status codes (will be overwritten with status-codes-blacklist if set) (default "200,204,301,302,307,401,403")|
|-b,|--status-codes-blacklist|string Negative status codes (will override status-codes if set)|
||--timeout duration|HTTP Timeout (default 10s)|
|-u,|--url string|The target URL|
|-a,|--useragent string|Set the User-Agent string (default "gobuster/3.1.0")|
|-U,|--username string|Username for Basic Auth|
|-d,|--discover-backup|Upon finding a file search for backup files|
||--wildcard|Force continued operation when wildcard found|

## vhost Mode Options[¶](https://3os.org/penetration-testing/cheatsheets/gobuster-cheatsheet/#vhost-mode-options "Permanent link")

| Short Switch | Long Switch           | Description                                                 |
| ------------ | --------------------- | ----------------------------------------------------------- |
| -h           | --help                | help for vhost                                              |
| -c           | --cookies string      | Cookies to use for the requests                             |
| -r           | --follow-redirect     | Follow redirects                                            |
| -H           | --headers stringArray | Specify HTTP headers, -H 'Header1: val1' -H 'Header2: val2' |
| -k           | --no-tls-validation   | Skip TLS certificate verification                           |
| -P           | --password string     | Password for Basic Auth                                     |
| -p           | --proxy string        | Proxy to use for requests [http(s)://host:port]             |
|              | --timeout duration    | HTTP Timeout (default 10s)                                  |
| -u           | --url string          | The target URL                                              |
| -a           | --useragent string    | Set the User-Agent string (default "gobuster/3.1.0")        |
| -U           | --username string     | Username for Basic Auth                                     |

## I. Finding subdomains


### **11. Google Dorking**

```
site:example.com -wwww -store 
```

```
site:example.com filetype:pdf password
```


### **12. crt.sh**

```
curl -sk "https://crt.sh/?q=%25.example.com&output=json" | jq -r '.[].name_value' | sed 's/\\n/\n/g' | grep -v "^\\*" | sort -u > crt_subdomains.txt
```


### **13. subfinder**

```
subfinder -d example.com -all -o subfinder_subdomains.txt
```

### **14. assetfinder**

```
assetfinder example.com | tee assetfinder_subdomains.txt
```

### **15. amass**

```
amass enum -d example.com > amass_subdomains.txt
```
### **16. Combine and Filter subdomains to get uniq subdomains**

```
cat crt_subdomains.txt subfinder_subdomains.txt assetfinder_subdomains.txt amass_subdomains.txt | grep example.com | sort -u | httprobe -prefer-https | grep https > example_alive.txt
```

## II. Screenshot

### **17. gowitness**

```
mkdir example_screenshot
gowitness file -f example_alive.txt -P example_screenshot --no-http
```

