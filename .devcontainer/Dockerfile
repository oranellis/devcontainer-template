# Base image with dependencies for C++ and Pico SDK
FROM ubuntu:latest

# Install required packages
RUN apt-get update && \
  apt-get install -y build-essential curl git python3 python3-pip sudo tar wget && \
  apt-get clean

# Install neovim
RUN wget https://github.com/neovim/neovim/releases/download/stable/nvim-linux64.tar.gz && \
  tar --strip-components=1 -xzf ./nvim-linux64.tar.gz -C /usr/ && \
  rm -r nvim-linux64.tar.gz

# Add a non-root user
RUN useradd -ms /bin/bash dev
RUN echo dev ALL=\(ALL\) NOPASSWD:ALL > /etc/sudoers.d/dev && \
  chmod 0440 /etc/sudoers.d/dev
USER dev

# Add dotfiles
RUN git clone --recursive -b cli --depth 1 https://github.com/oranellis/dotfiles /home/dev/dotfiles && \
  /home/dev/dotfiles/link.sh

# Install Pico SDK
RUN git clone --depth 1 https://github.com/raspberrypi/pico-sdk.git ~/pico-sdk && \
  echo "export PICO_SDK_PATH=~/pico-sdk" >> ~/.bashrc

# Set workspace
WORKDIR /workspace

