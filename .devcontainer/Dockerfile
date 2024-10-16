# Utilizamos la imagen base de Python
FROM mcr.microsoft.com/devcontainers/python:3.9

# Instalamos R y los paquetes necesarios
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    r-base r-base-dev && \
    R -e "install.packages(c('lme4', 'nlme', 'glmmTMB', 'emmeans', 'multcomp', 'MASS', 'ggplot2', 'patchwork', 'IRkernel'), repos='http://cran.rstudio.com/')" && \
    R -e "IRkernel::installspec()"

# Instalamos los paquetes de Python que mencionaste
RUN pip install jupyter statsmodels pandas numpy matplotlib seaborn
