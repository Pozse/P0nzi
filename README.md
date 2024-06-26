# AWS + T-Pot Honeypot Deployment

## Introduction

This project focuses on setting up a honeypot using AWS and T-Pot to detect unauthorized or malicious activity on a network. A honeypot mimics legitimate parts of an information system to lure potential attackers, revealing their methods and intentions. This enables the enhancement of security measures in real systems.

## Table of Contents

- [Introduction](#introduction)
- [Installation](#installation)
  - [AWS Setup](#aws-setup)
  - [T-Pot Installation](#t-pot-installation)
- [Usage](#usage)
- [Configuration](#configuration)
- [Security](#security)
- [Accessing the Dashboard](#accessing-the-dashboard)
- [Troubleshooting](#troubleshooting)
- [Contributors](#contributors)
- [License](#license)

## Installation

### AWS Setup

1. **Log into AWS**: Access the EC2 service.
2. **Select Ubuntu Server 24.04 LTS**: Choose an appropriate instance type based on your needs (e.g., `t2.micro` for free tier).
3. **Security Configuration**: Initially set your security group to allow SSH only from your IP.
4. **Storage Setup**: Allocate 30 GiB of `gp3` storage for the instance.

### T-Pot Installation

After setting up your Ubuntu instance on AWS:


sudo passwd ubuntu  # Set a root password

sudo apt update && sudo apt upgrade -y  # Update and upgrade the system

ssh-keygen  # Generate an SSH key

git clone https://github.com/dtag-dev-sec/t-pot-autoinstall.git

cd t-pot-autoinstall/

sudo su

./install.sh  # Follow the prompts during installation


## Usage

To manage your honeypot, use the following commands:


ssh -i "path/to/key.pem" ubuntu@your-instance-ip -p 64295


This command connects you to the T-Pot instance using a custom SSH port set during the installation.

## Configuration

Modify the security group settings as needed to enhance honeypot security:

1. **SSH Access**: Change the port to 64295.
2. **Web Dashboard Access**: Enable port 64297 for web access.

## Security

- Ensure that only your IP can access the SSH and web dashboard ports.
- Regularly update your security rules based on threat analysis.

## Accessing the Dashboard

Access the web dashboard through:

https://your-instance-ip:64297

Login with the username `ubuntu` and the password set during installation.

## Troubleshooting

If you encounter issues connecting to your instance or accessing the web dashboard, ensure your IP is correctly listed in your AWS security group settings.

## Contributors

- Pozse
