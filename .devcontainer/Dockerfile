FROM rocker/r-ver:4.1.2

# Instalar dependencias necesarias para R y Jupyter
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        curl \
        ca-certificates \
        git \
        libcurl4-openssl-dev \
        libssl-dev \
        libxml2-dev \
        libxt6 \
        libzmq3-dev \
        python3-pip \
    && apt-get autoremove -y && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# Instalar Jupyter y configuraciones para usar R con Jupyter
RUN python3 -m pip install setuptools \
    && python3 -m pip install jupyter \
    && R -e "install.packages(c('IRkernel'), repos='http://cran.rstudio.com/')" \
    && R -e "IRkernel::installspec(user = FALSE)"

# Asegurarse de que R esté en el PATH
ENV PATH="/usr/local/lib/R/bin:${PATH}"

# Usar un usuario no root para mayor seguridad
ARG USERNAME=docker
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Cambiar a usuario no root
USER $USERNAME
