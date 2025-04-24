# CSC180 Final Project: Python Supply Chain Exploit Lab #

## Overview

This project simulates a supply chain attack using a malicious Python package served from a local PyPI repository. The goal is to demonstrate how dependency confusion or internal package compromise can lead to **remote code execution (RCE)** during installation.

---

## Objective

To recreate a realistic attack scenario where:
- A developer unknowingly installs a **malicious package** instead of a trusted one.
- The package executes a payload during the install phase.
- We use Docker to contain the environment and replicate both the attack and the remediation.

---

## Setup Instructions

### Build the Lab Image
```bash
docker build -t csc180-exploit-lab .

Run the Exploit

docker run --rm csc180-exploit-lab




What I Did: Exploiting Python Package Installation (Dependency Confusion Attack)

This project demonstrates a simulated supply chain attack targeting the Python package installation process. Specifically, I recreated a dependency confusion vulnerability — a type of exploit where an attacker tricks a system into installing a malicious package instead of a trusted one.
The Goal

To show how a Python developer (or CI/CD pipeline) could accidentally install a malicious package that looks legitimate, and how that package can execute remote code without the developer realizing it.
How the Exploit Works

    I created a fake Python package called msgspec-python313-pre. The name mimics a real or internal dependency someone might mistakenly install.

    The package contains a hidden payload in its setup.py file — this is code that runs when the package is installed, not when it's imported or run normally.

    The payload writes a file (/tmp/pwned.txt) to simulate a breach. This proves that arbitrary code execution (RCE) occurred.

    I built a local PyPI-style repository inside a Docker container, so pip would install my malicious package instead of one from the internet.

    I wrote a Bash script (install.sh) that installs the malicious package and verifies if the exploit was successful by checking for the created file.

Why Docker?

Docker allows me to:

    Isolate the environment

    Simulate a real developer setup

    Reset everything on each run (safe & clean)

    Make the exploit easy to demo and reproduce

Why This Matters

This is based on real-world attacks, including ones used against companies like Microsoft, Apple, and Tesla. It shows how:

    A trusted dependency can be weaponized

    Supply chain attacks don’t need access to source code — just dependency injection

    Even simple install scripts can be dangerous
