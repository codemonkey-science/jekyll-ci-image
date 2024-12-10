# Use the Ubuntu base image
FROM ubuntu:22.04

# Create a non-root user with a home directory
RUN useradd -m jekyll

# Create and set permissions for GitHub Actions workspace directory
RUN mkdir -p /__w && \
    chown -R jekyll:jekyll /__w && \
    chmod -R 777 /__w

# Create and set permissions for temp directories
RUN mkdir -p /__w/_temp && \
    chown -R jekyll:jekyll /__w/_temp && \
    chmod -R 777 /__w/_temp

# Install system dependencies as root
RUN apt-get update && \
    apt-get install -y libyaml-dev build-essential zlib1g-dev libssl-dev \ 
    libreadline-dev libgdbm-dev libncurses5-dev libffi-dev libsqlite3-dev \
    libgmp-dev libxml2-dev libxslt1-dev libcurl4-openssl-dev libicu-dev \
    libjemalloc-dev && \
    rm -rf /var/lib/apt/lists/*

# Run container as the non-root user
USER jekyll

# Set the working directory to the GitHub Actions workspace
WORKDIR /__w
