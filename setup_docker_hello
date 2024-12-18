#!/bin/bash

set -e  # Exit immediately if a command exits with a non-zero status

# Check and fix dpkg interruptions
echo "Checking for dpkg interruptions..."
if sudo test -f /var/lib/dpkg/lock || sudo test -f /var/lib/dpkg/lock-frontend; then
    echo "Removing dpkg lock files..."
    sudo rm -f /var/lib/dpkg/lock
    sudo rm -f /var/lib/dpkg/lock-frontend
fi

if sudo test -f /var/cache/apt/archives/lock; then
    echo "Removing apt lock file..."
    sudo rm -f /var/cache/apt/archives/lock
fi

echo "Running 'dpkg --configure -a' to fix any interruptions..."
sudo dpkg --configure -a || echo "No interruptions to fix."

# Update package list and install prerequisites
echo "Updating package list and installing prerequisites..."
sudo apt-get update -y
sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common

# Add Docker's official GPG key
echo "Adding Docker's official GPG key..."
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add Docker's repository
echo "Adding Docker's repository..."
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list

# Install Docker
echo "Installing Docker..."
sudo apt-get update -y
sudo apt-get install -y docker-ce docker-ce-cli containerd.io

# Enable and start Docker service
echo "Enabling and starting Docker service..."
sudo systemctl enable docker
sudo systemctl start docker

# Verify Docker installation
echo "Verifying Docker installation..."
docker --version

# Run Docker's "Hello World" container
echo "Running Docker's 'Hello World' container..."
sudo docker run hello-world

# Search for a cool Tetris image
echo "Searching for a cool Tetris image..."
docker search tetris | grep uzyexe || echo "No image found, continuing with uzyexe/tetris."

# Pull the super cool Tetris image
echo "Pulling the super cool Tetris image..."
sudo docker pull uzyexe/tetris

# Run the super mega cool Tetris image
echo "Running the super mega cool Tetris image..."
sudo docker run -d -p 8080:80 uzyexe/tetris

# Get the public IP of the machine
IP=$(curl -s ifconfig.me)

# Display instructions to play Tetris
echo "Tetris is now running! Open your browser and visit:"
echo "http://$IP:8080"
