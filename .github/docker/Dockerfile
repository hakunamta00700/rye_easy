FROM ubuntu:latest

# Install basic dependencies
RUN apt-get update && apt-get install -y wget curl git python3 python3-pip gzip && rm -rf /var/lib/apt/lists/*

# Install Rye
RUN wget https://github.com/astral-sh/rye/releases/latest/download/rye-x86_64-linux.gz \
    && gunzip rye-x86_64-linux.gz \
    && chmod +x ./rye-x86_64-linux \
    && ./rye-x86_64-linux self install --yes \
    && echo 'export PATH="$HOME/.rye/shims:$PATH"' >> ~/.bashrc

# Set environment variables
ENV PATH="/root/.rye/shims:${PATH}"

# Install additional Python tools
RUN pip install --upgrade pip twine

# Set working directory
WORKDIR /github/workspace

# Default command
CMD ["bash"] 