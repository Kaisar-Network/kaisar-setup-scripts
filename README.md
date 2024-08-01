
# Kaisar Network setup scripts for Provider
This repository hosts a Bash script tailored to set up prerequisites necessary for the Kaisar Network. The script is adaptable across various Linux distributions and handles essential configurations, particularly for systems equipped with Nvidia GPUs.

## Getting Started
These guidelines will assist you in utilizing the setup script available in this repository.

### Prerequisites
Ensure that curl is installed on your system for script downloading purposes.

#### Ubuntu OS. 
If not already installed, execute the following command to install curl:
```bash
sudo apt install curl
```
#### Mac OS. 
```bash
coming soon
```
#### Windows OS. 
```bash
coming soon
```
### Installation

#### Ubuntu OS
Proceed with downloading the setup script using the command below:
```bash
curl -L https://github.com/kaisar-network/kaisar-setup-script_ubuntu.sh -o kaisar-setup.sh
```
Run the script to install driver, docker and required dependencies:
```bash
chmod +x kaisar-setup.sh && ./kaisar-setup.sh
```
Create a .env file in the root directory of your project and add the following environment variables
```
HTTP_PROVIDER=https://sepolia.infura.io/v3/0d02fbb6befa4284b5098ccb8c74e726
CONTRACT_ADDRESS_DEVICE_MANAGER=<<YourDeviceManagerContractAddress>>
CONTRACT_ADDRESS_ORDER_MANAGER=<<YourOrderManagerContractAddress>>
CONTRACT_ADDRESS_MAIN=<<YourMainContractAddress>>
WALLET_MAIN_ADDRESS=<<YourMainWalletAddress>>
SOCKET_URL=https://example.com
SOCKET_PATH=/csm/socket.io
JWT_TOKEN=<<Your Node Registration Token>>
```

Run follow script to start worker controller
```
docker run --env-file .env -d --name kaisar-worker  kaisarnetwork/worker-controller:latest
```

Check worker controller log
```
docker logs kaisar-worker
```

## Summary
The setup script executes a sequence of tasks:

- Sets up global variables and identifies the operating system along with its version.
- Checks for the presence of Nvidia GPUs and installs necessary drivers and the CUDA toolkit according to the detected Linux distribution and version.
- Installs Docker and Docker Compose while configuring Nvidia Docker if an Nvidia GPU is detected.
- Adds the user to the Docker group.
## Supported Distributions
This script supports the following distributions:

- Ubuntu (20.04, 22.04, 18.04)

## Contributions
Contributions to enhance this script are encouraged. Ensure that any pull requests or issues raised are pertinent to the script's functionality and compatibility.

## Support
For assistance, please raise an issue or contact our support team via [Telegram](https://t.me/kaisarnetwork).





