# Usage

Docker configurations for development of RG350M

# Commands

* `./commands/build_docker_image`: Create a docker image for development RG350M
* `./commands/create_docker_container`: Create a docker container named rg350m-dev
* `./commands/start_docker_container`: Start the docker container rg350m-dev
* `./commands/attach_docker_container`: Attach a new bash in the docker container rg350m-dev

# Binds

* `binds/buildroot`: The buildroot directory, will be mount as `/rg350m/buildroot` in the container
* `binds/commands`: The commands directory which contained in PATH environment in container, will be mount as `/rg350m/commands` in the container
* `binds/projects`: The projects directory, will be mount as `/rg350m/projects` in the container
* `binds/transfer`: The transfers directory to make an temporary place to transfer files between host and container, will be mount as `/rg350m/transfer` in the container
