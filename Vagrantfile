Vagrant.configure("2") do |config|
# Use Ubuntu 20.04 as the base box
config.vm.box = "ubuntu/focal64"

# Hostname of the virtual machine
config.vm.hostname = "airbnb-clone-vm"

# Forward ports from the VM to the host machine
config.vm.network :forwarded_port, guest: 5000, host: 5000 # Flask app port

# I expose the port 5001 of my vm to the port 5001 on my computer
config.vm.network :forwarded_port, guest: 5001, host: 5001 # API port

# Configure a private network
config.vm.network "private_network", type: "dhcp"

# Set up synced folders
config.vm.synced_folder ".", "/vagrant", type: "virtualbox"

# Provision the virtual machine
config.vm.provision "shell", inline: <<-SHELL
    # Update package lists
    sudo apt-get update

    # Python3 and pip
    sudo apt-get install -y python3 python3-pip

    # Flask and other dependencies
    sudo pip3 install flask flask_cors flasgger

    # Other project-specific dependencies
    sudo apt-get install -y python3-lxml

    # MySQL server
    sudo apt-get install -y mysql-server


SHELL
end
