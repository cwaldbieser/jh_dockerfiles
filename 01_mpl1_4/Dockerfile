# Build a Jupyterhub with matplotlib v1.4.
FROM jupyter/jupyterhub

# Add a notebook user.
RUN adduser --disabled-password --gecos '' hubuser
RUN echo 'hubuser:hubtest:::::' | newusers

# Copy config file.
COPY jupyterhub_config.py /srv/jupyterhub

# Install OS deps.
RUN apt-get update && apt-get install -y \
    virtualenvwrapper \
    libpng12-dev \
    libfreetype6-dev \
    python3-dev

# Create virtualenv
RUN /bin/bash -c 'source /usr/share/virtualenvwrapper/virtualenvwrapper.sh; mkvirtualenv -p /usr/bin/python3 jupyterenv3'
# Install python modules
RUN git clone git://github.com/matplotlib/matplotlib.git /srv/matplotlib
RUN /root/.virtualenvs/jupyterenv3/bin/pip install cython
RUN /root/.virtualenvs/jupyterenv3/bin/pip install python-dateutil
RUN /root/.virtualenvs/jupyterenv3/bin/python /srv/matplotlib/setup.py install 
RUN /root/.virtualenvs/jupyterenv3/bin/pip install pandas

# Install new kernel.
RUN mkdir -p /usr/local/share/jupyter/kernels/python3mpl
COPY kernel.json /usr/local/share/jupyter/kernels/python3mpl

