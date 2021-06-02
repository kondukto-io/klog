# klog

This is a simple leveled logging library (wrapper).

The usage is extremely simple, just set `klog.DefaultLogger.Level` with the desired level and call.  


### Sample program

```
package main

import (
	"flag"

	"github.com/kondukto-io/klog"
)

func main() {
	var debug bool
	flag.BoolVar(&debug, "debug", false, "debug")

	flag.Parse()

	if debug {
		klog.DefaultLogger.Level = klog.LevelDebug
	}

	klog.Println("regular print -- info")
	klog.Debug("this should print if debug flag is set")
	klog.Fatal("print fatal")
}
```

### Output
```
└> ./test -debug
2021-06-02T18:55:59+03:00 INF: regular print -- info
2021-06-02T18:55:59+03:00 DBG: this should print if debug flag is set
2021-06-02T18:55:59+03:00 ERR: print fatal

└> ./test
2021-06-02T18:56:37+03:00 INF: regular print -- info
2021-06-02T18:56:37+03:00 ERR: print fatal
```
