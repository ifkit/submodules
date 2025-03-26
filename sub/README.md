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
