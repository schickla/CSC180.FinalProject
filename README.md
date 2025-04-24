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
