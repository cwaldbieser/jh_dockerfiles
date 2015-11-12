# Build txcas on ubuntu 14.04.03
FROM ubuntu:14.04.3



# Install OS deps.
RUN apt-get update && apt-get install -y \
    virtualenvwrapper \
    build-essential \
    libffi-dev \
    libssl-dev \
    libxml2-dev \
    libxslt1-dev \
    python-dev \
    git

# Create virtualenv
RUN /bin/bash -c 'source /usr/share/virtualenvwrapper/virtualenvwrapper.sh; mkvirtualenv txcasenv'
# Clone txcas repo.
RUN git clone 'https://github.com/cwaldbieser/txcas.git' /srv/txcas
# Copy config files.
COPY cas.cfg /srv/txcas/cas.cfg
COPY cas.passwd /srv/txcas/cas.passwd
COPY serviceRegistry.json /srv/txcas/serviceRegistry.json
# Clone theme.
RUN git clone 'https://github.com/cwaldbieser/txcas_extras.git' /srv/txcas_extras
# Install python modules
RUN /root/.virtualenvs/txcasenv/bin/pip install -r /srv/txcas/requirements.txt

WORKDIR /srv/txcas
CMD ["/root/.virtualenvs/txcasenv/bin/twistd", "-n", "cas"]
