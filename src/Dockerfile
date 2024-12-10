# Use the Ubuntu base image
FROM ubuntu:22.04

# Create a non-root user with sudo access
RUN useradd -m jekyll && \
    apt-get update && \
    apt-get install -y sudo && \
    echo "jekyll ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/jekyll && \
    chmod 0440 /etc/sudoers.d/jekyll

# Create and set permissions for GitHub Actions workspace directory
RUN mkdir -p /__w && \
    mkdir -p /__w/_temp/_runner_file_commands && \
    mkdir -p /__w/_actions && \
    chown -R jekyll:jekyll /__w && \
    chmod -R 777 /__w

# Install system dependencies as root
RUN apt-get update && \
    apt-get install -y libyaml-dev build-essential zlib1g-dev libssl-dev \ 
    libreadline-dev libgdbm-dev libncurses5-dev libffi-dev libsqlite3-dev \
    libgmp-dev libxml2-dev libxslt1-dev libcurl4-openssl-dev libicu-dev \
    libjemalloc-dev && \
    rm -rf /var/lib/apt/lists/*

# Switch to non-root user
USER jekyll

# Set working directory to jekyll's home
WORKDIR /home/jekyll
