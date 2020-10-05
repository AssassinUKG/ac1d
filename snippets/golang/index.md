* [Home page](https://assassinukg.github.io/ac1d)
* [Snippets](https://assassinukg.github.io/ac1d/snippets)

# Go Snippets

### Build linux on windows
First check your enviroment
```powershell
go env
```
Look for "GOARCH and GOOS" : GOARCH=amd64, GOOS=windows
Open powershell and enter
```powershell
$env:GOOS = "linux"
```
Check your $env again to make sure its linux.
Then run, "go build" to build linux on windows (maybe be slower to include other libaries)
```powershell
go build
```

### Get Request
```golang
package main

import (
	"flag"
	"io/ioutil"
	"log"
	"net/http"
	"net/url"
)

func main() {
	// go run .\webrequest.go -url=https://golang.org/pkg/net/url/
	url := flag.String("url", "url", "Url to GET")
	flag.Parse()

	if isValidURL(*url) {
		resp, err := http.Get(*url)
		if err != nil {
			log.Fatal(err)
		}
		defer resp.Body.Close()
		if resp.StatusCode == 200 {
			bBytes, err := ioutil.ReadAll(resp.Body)
			if err != nil {
				log.Fatal(err)
			}
			outString := string(bBytes)
			print(outString)
		}
		print(resp.Body)
	} else {
		print("invalid Url")
	}
}

func isValidURL(testURL string) bool {
	_, err := url.ParseRequestURI(testURL)
	if err != nil {
		return false
	}
	u, err := url.Parse(testURL)
	if err != nil || u.Scheme == "" || u.Host == "" {
		return false
	}
	return true
}
```
