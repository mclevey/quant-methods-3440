FROM tiagopeixoto/graph-tool:latest

RUN pacman -Syu --noconfirm && \
    pacman -S --noconfirm \
    git \
    wget \
    curl \
    tree \
    unzip \
    openssh \
    python-pip \
    base-devel

# Install Quarto
RUN wget https://github.com/quarto-dev/quarto-cli/releases/download/v1.3.450/quarto-1.3.450-linux-amd64.tar.gz && \
    tar -xvzf quarto-1.3.450-linux-amd64.tar.gz && \
    cp -r quarto-1.3.450 /opt/quarto && \
    ln -s /opt/quarto/bin/quarto /usr/local/bin/quarto && \
    rm -rf quarto-1.3.450-linux-amd64.tar.gz quarto-1.3.450 \
    && quarto install tinytex

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 -

ENV PATH="/root/.local/bin:$PATH"

RUN curl -sS https://starship.rs/install.sh | sh -s -- -y \
    && echo 'eval "$(starship init bash)"' >> /root/.bashrc \
    && mkdir -p /workspace

WORKDIR /workspace
COPY pyproject.toml poetry.lock ./
RUN poetry install
