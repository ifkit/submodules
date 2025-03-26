# sub

| Module | Tag | `go get` | `import path` |
|-|-|-|-|
| `github.com/ifkit/submodules/sub`    | `sub/v1.2.3` | `go get github.com/ifkit/submodules/sub@v1.2.3`    | `github.com/ifkit/submodules/sub`    |
| `github.com/ifkit/submodules/sub/v2` | `sub/v2.3.4` | `go get github.com/ifkit/submodules/sub/v2@v2.3.4` | `github.com/ifkit/submodules/sub/v2` |

go.mod in the root is not required

it works even with git alone
```
GONOPROXY='github.com/ifkit/*' GOPRIVATE='github.com/ifkit/*' go get -x github.com/ifkit/submodules/sub/v2@v2.3.4
```

```
curl -s 'https://github.com/ifkit/submodules?go-get=1' | grep 'go-import'
  <meta name="go-import" content="github.com/ifkit/submodules git https://github.com/ifkit/submodules.git">
```


usage:
```
tail -n +1 *

==> go.mod <==
module subtest

go 1.24.1

require github.com/ifkit/submodules/sub v1.2.3

require github.com/ifkit/submodules/sub/v2 v2.3.4

==> go.sum <==
github.com/ifkit/submodules/sub v1.2.3 h1:J85vj47eatTQ47iWXOCK4/1zJ4Q/AP7G9tAnUN5eCGk=
github.com/ifkit/submodules/sub v1.2.3/go.mod h1:MMCFMIu5yHYdCA7E/vOhI1C+iD3qR+zCgOEg4TV9VGw=
github.com/ifkit/submodules/sub/v2 v2.3.4 h1:MKjaBKc2IpTSqAHsISdNVLaPtzCYfrBTAMAV+tbl58I=
github.com/ifkit/submodules/sub/v2 v2.3.4/go.mod h1:uRO+JXZsE/Af4xUtpxJtmqPuq7y0SICq6SKWu3gB+m8=

==> main.go <==
package main

import (
	"github.com/ifkit/submodules/sub"
	v2 "github.com/ifkit/submodules/sub/v2"
)

func main() {
	sub.Hello()
	v2.Hello()
}
```
