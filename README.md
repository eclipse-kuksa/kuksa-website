# kuksa-website
Sources of the Kuksa website

Generated GitHub Pages available at https://eclipse-kuksa.github.io/kuksa-website/.
In addition https://www.eclipse.org/kuksa/ can also be used as link to the generated pages.

## How to build

Make sure to check out the theme submodule

```
git submodule update --init
```

You can run a local instance for testing purposes like below.

```
$:~/kuksa-website$ hugo server -D -s .
Start building sites … 
hugo v0.111.3+extended linux/amd64 BuildDate=2023-03-16T08:41:31Z VendorInfo=debian:0.111.3-1
...
Web Server is available at http://localhost:1313/kuksa-website/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

