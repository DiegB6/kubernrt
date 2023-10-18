# Utilisez une image de base basée sur Debian Buster
FROM debian:buster

# Mettez à jour le système et installez les dépendances de base
RUN apt-get update && apt-get upgrade -y && apt-get install -y \
    python3-pip \
    git \
    wget \
    curl \
    bzip2 \
    telnet \
    debconf \
    locales \
    apt-utils \
    debconf-utils \
    iproute2 \
    isc-dhcp-client \
    net-tools \
    sudo \
    vim \
    nano \
    openssh-client \
    procps \
    man \
    httpie

# Configurez les locales pour le support UTF-8
ENV LC_ALL=fr_FR.UTF-8
ENV LANG=fr_FR.UTF-8
ENV LANGUAGE=fr_FR:fr
ENV LC_TIME=fr_FR.UTF-8
ENV LC_COLLATE=fr_FR.UTF-8

RUN echo "Europe/Paris" > /etc/timezone && \
    dpkg-reconfigure -f noninteractive tzdata && \
    sed -i -e 's/# fr_FR.UTF-8 UTF-8/fr_FR.UTF-8 UTF-8/' /etc/locale.gen && \
    echo 'LANG="fr_FR.UTF-8"'>/etc/default/locale && \
    dpkg-reconfigure --frontend=noninteractive locales && \
    update-locale LANG=fr_FR.UTF-8

# Copiez le code source de votre application Python dans le conteneur
WORKDIR /app
COPY . /app

# Installez les dépendances Python depuis un fichier requirements.txt
RUN pip3 install -r requirement.txt

# Définissez la commande de démarrage de votre application Python
CMD ["python3", "mon_script.py"]
