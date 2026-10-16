# Titan Cache Engine

A lightweight, high-performance in-memory cache core written in Rust with `#![no_std]`. I built this to experiment with low-level systems programming, lock-free concurrency, and bare-metal memory management.

## What's in here?

* **Lock-Free Map:** Uses atomic operations and Compare-And-Swap (CAS) to handle concurrent reads and writes without heavy mutexes.
* **Linear Probing:** Simple open-addressing collision resolution for fast slot mapping.
* **Fast Hash:** Built-in inline FNV-1a hash function to map keys directly to memory slots with zero heap allocations.
* **No Standard Library:** Written entirely for `#![no_std]` environments, making it suitable for embedded systems or low-level runtime experiments.

## How it works (Quick Overview)

Each slot in the map tracks its own state using an atomic variable:
- `0`: Empty (Available)
- `1`: Writing (Reserved via CAS)
- `2`: Committed (Ready to read)

## Status

This is a personal project and an experimental prototype. I'm just exploring how raw memory pointers, atomics, and concurrency primitives work under the hood in Rust. Feel free to look around, fork it, or play with the code!
