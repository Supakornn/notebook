---
title: Graceful Shutdown in Go
tags:
  - go
---

More info: https://victoriametrics.com/blog/go-graceful-shutdown

```go
c := make(chan os.Signal, 1)
signal.Notify(c, os.Interrupt, syscall.SIGTERM)

go func() {
    <-c
    log.Println("Shutting down server...")
    _ = s.app.Shutdown(context.Background())
    log.Println("Server stopped")
}()
```


