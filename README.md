# Go Concurrency Deadlock Example

This repository demonstrates a potential deadlock scenario in Go when using channels and wait groups for concurrent operations.

## The Bug

The `bug.go` file contains a program that attempts to send data from one goroutine to another using a channel. However, there's a race condition that can cause the program to deadlock.  The reader goroutine might finish before the writer goroutine closes the channel, leading to the reader blocking indefinitely.

## The Solution

The `bugSolution.go` file provides a corrected version of the program. It addresses the deadlock by ensuring that the channel is properly closed before the wait group is done.

## How to Reproduce

1. Clone this repository.
2. Navigate to the repository directory.
3. Run `go run bug.go` to observe the deadlock (potential). It may or may not deadlock on every run, highlighting the race condition's unpredictable nature.
4. Run `go run bugSolution.go` to see the corrected, deadlock-free version.

## Lessons Learned

This example highlights the importance of careful channel management in concurrent Go programs.  Proper use of `close()` and avoiding race conditions is crucial to prevent deadlocks and ensure correct program behavior.