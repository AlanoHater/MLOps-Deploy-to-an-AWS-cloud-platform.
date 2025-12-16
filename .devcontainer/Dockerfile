# 1. Usa la imagen base completa para asegurar que todas las herramientas de compilación estén disponibles
FROM python:3.8

# Establece el directorio de trabajo dentro del contenedor
WORKDIR /workspace

# Instala dependencias del sistema necesarias para compilar paquetes como scikit-learn, dvc, y ssh.
# Luego, elimina el caché de paquetes para reducir el tamaño de la imagen.
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        build-essential \
        git \
        libssl-dev \
        libffi-dev \
        openssh-client \
    && rm -rf /var/lib/apt/lists/*

# Copia los archivos de requisitos e instala las dependencias de Python
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copia el resto del código del proyecto
COPY . .

# Expone el puerto por defecto para la aplicación FastAPI (MLEM deploy)
EXPOSE 8000

# Por defecto, ejecuta el shell
CMD ["/bin/bash"]