# Usamos la imagen base de Python
FROM mcr.microsoft.com/devcontainers/python:3.9

# Instalamos R y dependencias necesarias
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    r-base r-base-dev libcurl4-openssl-dev libssl-dev libxml2-dev && \
    R -e "install.packages(c('lme4', 'nlme', 'glmmTMB', 'emmeans', 'multcomp', 'MASS', 'ggplot2', 'patchwork', 'IRkernel'), repos='http://cran.rstudio.com/')" && \
    R -e "IRkernel::installspec(user = FALSE)"

# Instalamos los paquetes de Python necesarios
RUN pip install jupyter statsmodels pandas numpy matplotlib seaborn

# Configuramos el Jupyter Notebook para asegurarnos de que use R y Python
RUN jupyter notebook --generate-config
