# VagrantVM Infrastructure as Code

## Introduction
This repository contains Infrastructure as Code (IaC) configurations using **Vagrant** to provision and manage virtual machines (VMs). Vagrant simplifies the creation and management of development environments by automating VM provisioning and configuration, ensuring consistency and repeatability across environments.

## Key Features
- **Multi-VM Support**: Define and provision multiple VMs simultaneously.
- **Cross-Platform**: Works seamlessly across Windows, macOS, and Linux systems.
- **Provisioning**: Automates software installation and configuration using Shell scripts, Ansible, or other provisioning tools.
- **Version Control**: All configurations are stored as code and managed using Git, enabling version control and collaboration.
- **Consistency**: Ensures development environments are identical across all team members.

## Prerequisites
Before using this repository, ensure the following tools are installed on your system:

1. [Vagrant](https://www.vagrantup.com/)
2. [VirtualBox](https://www.virtualbox.org/) (or another supported provider)
3. [Git](https://git-scm.com/)

## Getting Started

### Clone the Repository
```bash
git clone https://github.com/DevOps-1312/Vagrant_VMS.git
cd Vagrant_VMS
```

### Initialize the Environment
Run the following command to initialize the environment:
```bash
vagrant up
```
This command will:
- Download the required base boxes (if not already available).
- Provision the VMs based on the configurations in the `Vagrantfile`.

### Accessing the VMs
To SSH into a specific VM, use the following command:
```bash
vagrant ssh <vm_name>
```
Replace `<vm_name>` with the name of the VM defined in the `Vagrantfile`.

### Stopping and Destroying VMs
To stop the VMs without destroying them:
```bash
vagrant halt
```

To destroy all VMs and free up system resources:
```bash
vagrant destroy
```

## Project Structure
```
.
├── Vagrantfile         # Main configuration file for Vagrant
├── scripts/            # Provisioning scripts (e.g., shell scripts, Ansible playbooks)
├── configs/            # Additional configuration files (e.g., environment variables)
└── README.md           # Project documentation
```

## Customization
Modify the `Vagrantfile` to:
- Add or remove VMs.
- Customize VM specifications (CPU, RAM, Disk, etc.).
- Change the base box or networking configurations.

Example:
```ruby
Vagrant.configure("2") do |config|
  config.vm.define "web" do |web|
    web.vm.box = "ubuntu/bionic64"
    web.vm.network "private_network", ip: "192.168.33.10"
    web.vm.provision "shell", path: "scripts/setup-web.sh"
  end
end
```

## Troubleshooting
- **Error: Provider Not Found**: Ensure VirtualBox (or another provider) is installed and configured properly.
- **Networking Issues**: Check for conflicts in IP addresses or ports.
- **Slow Performance**: Allocate more CPU and RAM to the VMs in the `Vagrantfile`.

## Contributing
We welcome contributions! Feel free to submit issues or pull requests to improve this repository.

## License
This project is licensed under the [MIT License](LICENSE).

## Contact
For any questions or support, please contact the repository maintainers.

---

Happy Vagrating! 🚀
