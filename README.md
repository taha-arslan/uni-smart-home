# Security-Focused Smart Home

A small smart-home prototype where every command between a Python dashboard and an Arduino board is **authenticated with a token and encrypted** before being sent over USB serial. Built as a university project.

## The problem
Most low-cost smart-home devices send commands with no encryption or authentication. An attacker who can access the connection can read or forge a command (for example, unlock a door). This project shows how to close that gap on a small, controlled system.

## What it does
- A **PIR motion sensor**, a **relay** (simulating a door lock) and **two LEDs**, driven from a Python dashboard.
- Every command is **authenticated with a token** and **encrypted** (XOR + hex) before being sent over USB serial.
- A wrong or missing token is **rejected**, and encrypted traffic is unreadable on the wire.

## Tech
- **Python** (dashboard, `pyserial`)
- **Arduino / C++** (board side, SparkFun RedBoard)
- **USB serial** communication

## How it works
1. The dashboard builds a command in the format `COMMAND:TOKEN`.
2. The message is encrypted and sent over serial.
3. The board decrypts it, checks the token, and only then acts (LED / relay).
4. A wrong token is rejected before any action.

## Demo
- Wrong token rejected: [video link]
- Plaintext vs encrypted traffic: [video link]

## Note
This is an educational project. The token and key are placeholders (`YOUR_TOKEN_HERE`, `YOUR_KEY_HERE`), set your own before running.
