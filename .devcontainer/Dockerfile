FROM ubuntu:24.04

SHELL ["/bin/bash", "-c"]

RUN apt-get update && apt-get install -y \
    bash-completion \
    verilator \
    build-essential \
    python3 \
    python3-pip \
    python3-venv \
    git \
    wget \
    sudo \
    vim \
    && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# 2. Install Python packages for TL-Verilog development
#COPY requirements.txt /workspace/mate-v/requirements.txt
#RUN pip install -r requirements.txt

RUN groupadd --gid 1001 vscode \
    && useradd -p "" --uid 1001 --gid vscode --shell /bin/bash --create-home vscode
RUN usermod -aG sudo vscode

USER vscode
ENV HOME=/home/vscode

RUN pip install makerchip-app \
    setuptools \
    sandpiper-saas \
    --break-system-packages

ENTRYPOINT ["/bin/bash","-c"]
CMD ["bash"]
