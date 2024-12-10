# Use the Ubuntu base image
FROM ubuntu:22.04

# Create a non-root user with a home directory
RUN useradd -m ansible

# Install system dependencies as root
RUN apt-get update && \
    apt-get install -y libyaml-dev build-essential zlib1g-dev libssl-dev \ 
    libreadline-dev libgdbm-dev libncurses5-dev libffi-dev libsqlite3-dev \
    libgmp-dev libxml2-dev libxslt1-dev libcurl4-openssl-dev libicu-dev \
    libjemalloc-dev && \
    rm -rf /var/lib/apt/lists/*

# Set up virtual environment and install Ansible as the non-root user
USER jekyll

# Set the working directory to the non-root user's home directory
WORKDIR /home/jekyll
