FROM rocker/r-ver:4.1.2

# [Option] Install zsh
ARG INSTALL_ZSH="true"
# [Option] Upgrade OS packages to their latest versions
ARG UPGRADE_PACKAGES="false"

# Install needed packages and setup non-root user. Use a separate RUN statement to add your own dependencies.
ARG USERNAME=docker
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        zsh \
        curl \
        ca-certificates \
        git \
        libzip-dev \
        libcurl4-openssl-dev \
        libssl-dev \
        libxml2-dev \
        python3-pip \
        libxt6 \
        libzmq3-dev \
    && apt-get autoremove -y && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# Create a non-root user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

RUN python3 -m pip install setuptools
RUN python3 -m pip install radian
RUN python3 -m pip install jupyter
RUN R -e "install.packages(c('IRkernel', 'devtools'), repos='http://cran.rstudio.com/')"
RUN R -e "IRkernel::installspec(user = FALSE)"

# Asegúrate de que R esté en el PATH
ENV PATH="/usr/local/lib/R/bin:${PATH}"

# Switch to non-root user
USER $USERNAME
