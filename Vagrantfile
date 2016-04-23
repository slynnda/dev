# Configuration constants:
CONFIG_VERSION = "2"
VAGRANT_VERSION = "1.8.1"
BOX = "ubuntu/trusty64"
BOX_CHECK_UPDATE = true
BOOTSTRAP_FROM = "bootstrap.sh"
HOSTNAME = "dev"
POST_UP_MESSAGE = "Boot completed! Dev VM is up and running!"
GUEST_PORT = 8081
HOST_PORT = 4567

# Environment constants:
LOCALE = "en_US.UTF-8"
ENV_TO_FORWARD = []

# Environment overrides:
ENV["LC_ALL"] = LOCALE

# Configure VM:
Vagrant.require_version VAGRANT_VERSION
Vagrant.configure(CONFIG_VERSION) do |config|
  config.vm.box = BOX
  config.vm.box_check_update = BOX_CHECK_UPDATE
  config.vm.hostname = HOSTNAME
  config.vm.provision :shell, path: BOOTSTRAP_FROM
  config.vm.post_up_message = POST_UP_MESSAGE
  config.vm.network :forwarded_port, guest: GUEST_PORT, host: HOST_PORT
end

# Configure ssh:
Vagrant.configure(CONFIG_VERSION) do |config|
  config.ssh.forward_env = ENV_TO_FORWARD
end
