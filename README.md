# EvalDeployMLToRPI
Just testing the bones of creating a pipeline to compile, deploy and manage from github via VS Code


🚀 Setup Steps
Create a directory for your stack:

bash
mkdir -p ~/rpi-stack && cd ~/rpi-stack
Save the above YAML as docker-compose.yml.

Create necessary folders for volumes:

bash
mkdir -p etc-pihole etc-dnsmasq.d scrypted mosquitto/config mosquitto/data mosquitto/log
Start the containers:

bash
docker compose up -d

COMMANDS RAN TO INSTALL DOCKER & COMPOSE ON MY RPI4

1. Update and Upgrade your system:
It is recommended to start by ensuring your Raspberry Pi OS is up-to-date.
Code

sudo apt update && sudo apt upgrade -y
2. Install Docker Engine:
The official Docker installation script is a common and convenient method.
Code

curl -fsSL https://get.docker.com | sh
3. Add your user to the docker group:
This allows you to run Docker commands without sudo.
Code

sudo usermod -aG docker $USER
You will need to log out and log back in (or restart your Raspberry Pi) for this change to take effect.
4. Install Docker Compose:
There are a couple of ways to install Docker Compose:
Using pip (older method, for Docker Compose v1):
Code

    sudo apt install python3-pip -y
    pip3 install docker-compose
Installing the Docker Compose Plugin (recommended for Docker Compose v2):
If you are running a recent version of Raspberry Pi OS (e.g., Bookworm) and want the modern docker compose command, you can install the plugin:
Code

    sudo apt install docker-compose-plugin -y
Alternatively, you can manually download the binary for the correct architecture (aarch64 for 64-bit OS, armv7 for 32-bit OS) from the Docker Compose GitHub releases page and place it in your /usr/local/bin/ directory, ensuring it is executable.
5. Verify the installation:
docker.
Code

    docker run hello-world
This command downloads and runs a test container, confirming Docker is working. docker compose.
Code

    docker compose version
or (for older installations)
Code

    docker-compose --version
This displays the installed Docker Compose version.
6. Enable Docker to start on boot (optional but recommended):
Code

sudo systemctl enable docker