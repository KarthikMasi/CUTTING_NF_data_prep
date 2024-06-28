BootStrap: docker
From: ubuntu:latest

%help
    This container installs the latest version of dcm2niix on an Ubuntu base.

%post
    # Update package list and install dependencies
    apt-get update && apt-get install -y \
        git \
        cmake \
        g++ \
        make \
        curl \
        libopenjp2-7-dev \
        libgomp1

    # Clone the dcm2niix repository from GitHub
    git clone https://github.com/rordenlab/dcm2niix.git /opt/dcm2niix

    # Build dcm2niix
    cd /opt/dcm2niix
    mkdir build
    cd build
    cmake ..
    make
    mkdir -p /inputs /outputs

    # Install dcm2niix
    make install

    # Clean up
    apt-get clean
    rm -rf /var/lib/apt/lists/*

%environment
    export PATH=/usr/local/bin:$PATH

%runscript
    exec dcm2niix "$@"
