<img src="/misc/omgossh.png" alt="oh my gossh" />

**Oh My GoSSH** is a simple library for **Golang** which allows you to connect via ssh to any remote server using username and password.

**Use at your own risk**.

# Usage

```go
package main

import (
  "fmt"
  omgossh "github.com/micheleriva/omgossh"
)

const SSH_HOST     = os.Getenv("SSH_HOST")
const SSH_USERNAME = os.Getenv("SSH_USERNAME")
const SSH_PASSWORD = os.Getenv("SSH_PASSWORD")

func main() {

  conn, err := omgossh.Connect(SSH_HOST, SSH_USERNAME, SSH_PASSWORD)
  if err != nil {
    log.Fatal(err)
  }

  stdout, err := conn.Exec("cd /myDir", "ls -la")
  if err != nil {
    log.Fatal(err)
  }

  fmt.Println(stdout)
}
```

```bash
go run .

# Now we should see the result of "cd /myDir" and "ls -la" commands
drwxr-xr-x  7 root root  224 Sep 16 20:15 ./
drwxr-xr-x  8 root root  256 Sep 16 20:15 ../
-rw-r--r--  1 root root  691 Sep 16 20:15 README.md
```

# License
[GPLv3](/LICENSE.md)