# Netfilter

[![GoDoc](https://godoc.org/github.com/juliengk/go-netfilter/iptables?status.svg)](https://godoc.org/github.com/juliengk/go-netfilter/iptables)

## Example

```go
import (
	"fmt"
	"os"

	"github.com/juliengk/netfilter/iptables"
)

func main() {
	ipt, err := iptables.New(4, false)
	if err != nil {
		fmt.Println(err)
		os.Exit(1)
	}

	opts := iptables.ListOptions {
		Chain: "OUTPUT",
		Verbose: true,
		Numeric: true,
		LineNumbers: true,
	}

	rules, err := ipt.List("filter", &opts)
	if err != nil {
		fmt.Println(err)
		os.Exit(1)
	}

	fmt.Println(rules)
}
```
