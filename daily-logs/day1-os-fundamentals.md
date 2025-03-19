# Day 1: Getting Started with Operating Systems Concepts

**Date**: March 18, 2025

---

## Today's Focus
- Operating systems fundamentals and development environment setup.

---

## What I Learned
- Read Chapters 1-2 of **"Operating Systems: Three Easy Pieces"**.
- Key OS abstractions:
  - **Virtualization**
  - **Concurrency**
  - **Persistence**
- Historical context of OS development.
- The concept of **system calls** as the API between user programs and the OS.

---

## Implementation Work

### Development Environment Setup
- Installed the latest **GCC compiler** and build tools.
- Configured **Rust** development environment with `cargo`.
- Installed **QEMU** for future kernel experimentation.

### Project Work
- Created initial project structure for my simple shell implementation.
- Wrote first code to handle basic command parsing:

```rust
// Example Rust code for command parsing
# Simple Shell Implementation in Rust

Below is a basic implementation of a shell in Rust. This snippet demonstrates how to read user input, execute commands, and handle errors.

## Code Snippet

```rust
use std::io::{stdin, stdout, Write};
use std::process::{Command, exit};

fn main() {
    loop {
        // Display prompt
        print!("> ");
        stdout().flush().unwrap();
        
        // Read command
        let mut input = String::new();
        stdin().read_line(&mut input).unwrap();
        
        // Process command
        let command = input.trim();
        if command == "exit" {
            exit(0);
        }
        
        // Execute command (basic implementation)
        match Command::new(command).spawn() {
            Ok(mut child) => {
                child.wait().unwrap();
            },
            Err(e) => {
                eprintln!("Error: {}", e);
            }
        }
    }
}

```
---

# Challenges Faced

- Understanding the distinction between **process scheduling** and **CPU virtualization**.
- Properly handling command execution in Rust with appropriate error handling.
- Setting up the right development environment for low-level programming.

---

## Resources Used

- [Operating Systems: Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/)
- [The Rust Programming Language Book](https://doc.rust-lang.org/book/)
- [Linux man pages for system calls](https://man7.org/linux/man-pages/)

---

## Tomorrow's Plan

- Read **OSTEP Chapters 3-4** on process concepts.
- Continue shell implementation with proper command parsing and execution.
- Implement basic built-in commands like `cd`, `pwd`, and `exit`.

---

## Reflections

Today I realized how much my web development experience has kept me abstracted from the underlying OS. Building a shell is already helping me see how programs actually interact with the kernel. I'm excited to understand how processes are created and managed by the OS.