### Install
```
go get -u github.com/gofiber/fiber
go get -u github.com/gofiber/recover
```
### Example
```go
package main

import (
  "github.com/gofiber/fiber"
  "github.com/gofiber/recover"
)

func main() {
  app := fiber.New()

  cfg := logger.Config{
    // Optional
    Handler: func(c *fiber.Ctx, err error) {
      c.SendString(err.Error())
      c.SendStatus(500)
    }
  }

  app.Use(recover.New(cfg))

  app.Get("/", func(c *fiber.Ctx) {
    panic("Hi, I'm a error!")
  })

  app.Listen(3000)
}
```
### Test
```curl
curl http://localhost:3000
```
