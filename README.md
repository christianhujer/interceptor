# interceptor
Go library to intercept stdout and stderr, useful in testing.

## Example
Given the following main program
```
package hello

import "fmt"

func main() {
    fmt.Println("Hello, world!")
}
```

Here's how to test it:
```
package hello

import (
	. "github.com/christianhujer/assert"
	"github.com/christianhujer/interceptor"
	"testing"
)

func TestHello(t *testing.T) {
	stdout, stderr, err := interceptor.InterceptStrings(main)
	AssertEquals(t, "Hello, world!\n", *stdout)
	AssertEquals(t, "", *stderr)
	AssertEquals(t, nil, err)
}
```
