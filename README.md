# AutoDock

Tools included in the container are MGL Tools and AutoDock Vina. Two versions available: NVIDIA and NOUVEAU-supported container. For NVIDIA support, you need to install NVIDIA driver on host and install nvidia-docker2.

To download:
  1. docker pull afandiadib/autodock:nvidia
  2. docker pull afandiadib/autodock:nouveau

Example of usage:

### AutoDock Tools - nouveau

To run autodock tools:
docker run --rm --user=$(id -u) --env=DISPLAY --workdir=\`pwd\` --volume=/home/$USER:/home/$USER --volume=/media:/media --volume=/mnt:/mnt --volume=/etc/group:/etc/group:ro --volume=/etc/passwd:/etc/passwd:ro --volume=/etc/shadow:/etc/shadow:ro --volume=/etc/sudoers.d:/etc/sudoers.d:ro --volume=/tmp/.X11-unix:/tmp/.X11-unix:rw --volume=/usr/share/icons:/usr/share/icons --device=/dev/dri afandiadib/autodock:nouveau adt

If permission denied, you need to change ownership of /dev/dri on host for gpu acceleration.
sudo chown -R $USER /dev/dri

### AutoDock Tools - nvidia

To run autodock tools:
docker run --rm --user=$(id -u) --env=DISPLAY --workdir=\`pwd\` --volume=/home/$USER:/home/$USER --volume=/media:/media --volume=/mnt:/mnt --volume=/etc/group:/etc/group:ro --volume=/etc/passwd:/etc/passwd:ro --volume=/etc/shadow:/etc/shadow:ro --volume=/etc/sudoers.d:/etc/sudoers.d:ro --volume=/tmp/.X11-unix:/tmp/.X11-unix:rw --volume=/usr/share/icons:/usr/share/icons --runtime=nvidia afandiadib/autodock:nvidia adt


### Autodock Vina - nouveau

To run vina, alias the docker command in .bashrc for convenience:

alias vina='docker run --rm --workdir=\`pwd\` --volume=\`pwd\`:\`pwd\` afandiadib/autodock:nouveau vina'

For virtual screening, it is better to run interactively though.


