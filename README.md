# packer-parallel-build

# Install Packer

Create a directory named packer_tutorial and paste the following configuration into a file named docker-ubuntu.pkr.hcl

# Initialize the Packer template.
packer init .

To use parallel builds, create a source then add the source to the sources array in the build block. Your sources do not need to be the same type. This tells Packer to build multiple images when that build is run.

Add the following source block to your docker-ubuntu.pkr.hcl file. Do not replace the existing ubuntu source; add it underneath.

source "docker" "ubuntu-bionic" {
  image  = "ubuntu:bionic"
  commit = true
}

Then update your build block to use the new source.

# Build images
packer build .
