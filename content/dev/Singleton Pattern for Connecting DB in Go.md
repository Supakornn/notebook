---
title: Singleton Pattern for Connecting DB in Go
tags:
  - go
---
More info: https://www.codingexplorations.com/blog/implementing-the-singleton-pattern-in-go

```go
var instance *sql.DB
var once sync.Once

func GetDB() *sql.DB {
    once.Do(func() {
        db, err := sql.Open("postgres", "connection string")
        if err != nil {
            log.Fatalf("Failed to connect: %v", err)
        }
        instance = db
    })
    return instance
}
```

