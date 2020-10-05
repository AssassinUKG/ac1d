[Home page](https://assassinukg.github.io/ac1d)
[Snippets](https://assassinukg.github.io/ac1d/snippets)

### Go Snippets

# Build linux on windows
First check your enviroment
```
go env
```
Look for "GOARCH and GOOS" : GOARCH=amd64, GOOS=windows
Open powershell and enter
```
$env:GOOS = "linux"
```
Check your $env again to make sure its linux.
Then run, "go build" to build linux on windows (maybe be slower to include other libaries)
```
go build
```

