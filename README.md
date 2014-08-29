# goamz - An Amazon Library for Go

This is a fork of [https://github.com/torrancew/goamz](https://github.com/mitchellh/goamz)
that adds some missing API calls to certain packages.

It adds the following features on top of mitchell's library:
  * Allows configuration of custom SSL CA (S3)

## Example Usage

```go
package main

import (
  "github.com/torrancew/goamz/aws"
  "github.com/torrancew/goamz/s3"
  "log"
  "fmt"
)

func main() {
  auth, err := aws.EnvAuth()
  if err != nil {
    log.Fatal(err)
  }
  client := s3.New(auth, aws.USEast)
  resp, err := client.ListBuckets()

  if err != nil {
    log.Fatal(err)
  }

  log.Print(fmt.Sprintf("%T %+v", resp.Buckets[0], resp.Buckets[0]))
}
```
