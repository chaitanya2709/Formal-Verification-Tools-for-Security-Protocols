# Installation Guide for Formal Verification Tools

This document provides step-by-step instructions for installing Tamarin-Prover, a formal verification tool for security protocols.

---

## System Requirements

- Linux-based operating system
- Maude (version newer than 2.4)
- Stack
---

## 1. Installation of Tamarin Prover

This guide is intended for Debian/Ubuntu-based Linux distributions.

### 1.1 Install Homebrew (Linuxbrew)

Installs **Homebrew**, a package manager for Linux.
Homebrew is used because **Tamarin Prover is officially distributed via Homebrew**, even on Linux systems.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
---

### 1.2 Add Homebrew to the Shell Environment

Adds Homebrew environment variables to your `.bashrc` file so that it is available every time you open a terminal
```bash
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> ~/.bashrc
```
---

### 1.3 Activate Homebrew in the Current Session

Makes the `brew` command available **immediately**, without restarting the terminal.
```bash
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"
```
---

### 1.4 Install System Build Tools

Installs essential development tools such as:

* `make`
* `gcc`
* `g++`

These are required to compile dependencies used by Tamarin.
```bash
sudo apt-get update
sudo apt-get install build-essential
```
---

### 1.5 Install GCC via Homebrew

Installs a **modern version of GCC** through Homebrew. This avoids compatibility issues with older system compilers.
```bash
brew install gcc
```
---

### 1.6 Install Tamarin Prover

Downloads and installs the **Tamarin Prover** tool itself. After this step, the command `tamarin-prover` becomes available.
```bash
brew install tamarin-prover/tap/tamarin-prover
```
---

### 1.7 Install Supporting Dependencies

Installs additional tools used by Tamarin:

* **Maude** – term rewriting engine (used internally)
* **Graphviz** – for visualizing protocol execution graphs
* **Haskell Stack** – required for some Tamarin components

These are **recommended** for full functionality.
```bash
brew install tamarin-prover/tap/maude graphviz haskell-stack
```
---

### 1.8 Run Tamarin Prover

Starts Tamarin Prover in **interactive GUI mode** (The interactive mode opens a local web interface), allowing you to:

* Load `.spthy` protocol files
* Explore rules and traces
* Prove security lemmas step by step

The `.` means use the current directory (where your `.spthy` file is located).

```bash
tamarin-prover interactive .
```
---


## Summary

Tamarin Prover was installed on Linux using Homebrew. First, Homebrew was installed and added to the shell environment. Required build tools and a modern GCC compiler were then installed. The Tamarin Prover and its dependencies, including Maude and Graphviz, were installed via Homebrew. Finally, Tamarin Prover was executed in interactive mode to model and verify the security properties of the proposed protocol.
---

## Our System Configuration

- Ubuntu 24.04.3 LTS
- opam 2.1.5
- ocaml 4.14.1
- maude 2.7.1 (>=2.4)
- graphviz 14.1.1
- stack 3.7.1

**OPAM** and **OCaml** are only required when building Tamarin from source or when modifying the prover itself.

When using a **precompiled binary** or the **official Docker image**, OPAM and OCaml are not required on the host system.
---

## References

Official site of Tamarin-Prover
- https://tamarin-prover.com/

Git Source code repository
- https://github.com/tamarin-prover/tamarin-prover/tree/master

Sample Tutorial for execution
- https://youtu.be/XptJG19hDcQ?si=2IdJzK1cgDf3vBPH

## Disclaimer :

This repository contains personal installation notes for academic and research purposes.
All software, names, and trademarks belong to their respective owners.
