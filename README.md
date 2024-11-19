# Duplicate Packet Generator for UDP and ICMP on Linux Kernel

## Overview

This repository contains code to create duplicate packets for UDP and ICMP protocols within the Linux kernel. The modified kernel code sends duplicate packets over a specified interface.

## Prerequisites

- **Operating System:** Ubuntu 22.04
- **Kernel Version:** 5.15.0

## Installation Instructions

### 1. Install the Required Kernel Version

Ensure you have the correct kernel version installed:

```bash
sudo apt install linux-image-5.15.0-50-generic
