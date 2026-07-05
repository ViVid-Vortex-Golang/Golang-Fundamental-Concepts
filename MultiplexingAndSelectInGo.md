# Multiplexing and `select` in Go

Multiplexing means **fast switching between multiple tasks at hand in Go**.

## A goroutine is switched out when it is:

1. Waiting for something
   - Channel receive/send
   - Network I/O
   - File I/O
   - `time.Sleep`

### Example

```go
ch <- 10 // goroutine waits if no receiver
```

or

```go
time.Sleep(1 * time.Second)
```

👉 At this point, Go says:

> "You are waiting anyway, I'll use the CPU for another goroutine."

---

# What is `select` in Go?

👉 `select` is a control structure that lets a goroutine wait on **multiple channel operations at the same time**.

Think:

> "I'm ready to do A, B, or C — whichever becomes ready first, I'll do that."

---

## Example with real behavior

```go
ch1 := make(chan string)
ch2 := make(chan string)

go func() {
    ch1 <- "from ch1"
}()

go func() {
    ch2 <- "from ch2"
}()

select {
case msg := <-ch1:
    fmt.Println(msg)

case msg := <-ch2:
    fmt.Println(msg)
}
```

👉 Only **ONE** case runs — whichever channel is ready first.
