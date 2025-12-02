FROM node:20

# Install basic development tools and Python
RUN apt update && apt install -y less man-db sudo python3 python3-pip python3-venv

# Create symlinks for python commands
RUN ln -sf /usr/bin/python3 /usr/bin/python

# Ensure default `node` user has access to `sudo`
ARG USERNAME=node
RUN echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Set `DEVCONTAINER` environment variable to help with orientation
ENV DEVCONTAINER=true
