# StaticBin [![GoDoc](https://godoc.org/github.com/olebedev/staticbin?status.png)](https://godoc.org/github.com/olebedev/staticbin)

[Gin](https://github.com/gin-gonic/gin) middleware/handler for serving static files from binary data.  
Based on [staticbin](https://github.com/martini-contrib/staticbin) by [@yosssi](https://github.com/yosssi).  

## Usage

```go
package main

import (
  "github.com/gin-gonic/gin"
  "github.com/olebedev/staticbin"
)

func main() {
  r := gin.New() // without any middlewares

  // Serves the "static" directory's files from binary data.
  // You have to pass the "Asset" function generated by
  // go-bindata (https://github.com/jteeuwen/go-bindata).
  r.Use(staticbin.Static(Asset, staticbin.Options{
    Dir: "static",
  }))

  r.Get("/", func() string {
    return "Hello world!"
  })

  r.Run(":8080")
}
```