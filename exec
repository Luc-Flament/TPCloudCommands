#!/bin/bash

set -e  # Exit immediately if a command exits with a non-zero status

# Update package list and install prerequisites
echo "Updating package list and installing prerequisites..."
apt-get update -y
apt-get install -y apt-transport-https ca-certificates curl software-properties-common

# Add Docker's official GPG key
echo "Adding Docker's official GPG key..."
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add Docker's repository
echo "Adding Docker's repository..."
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list

# Install Docker
echo "Installing Docker..."
apt-get update -y
apt-get install -y docker-ce docker-ce-cli containerd.io

# Enable and start Docker service
echo "Enabling and starting Docker service..."
systemctl enable docker
systemctl start docker

# Verify Docker installation
echo "Verifying Docker installation..."
docker --version

# Run Docker's "Hello World" container
echo "Running Docker's 'Hello World' container..."
docker run hello-world

echo "Setup complete. Docker is installed and running successfully."
