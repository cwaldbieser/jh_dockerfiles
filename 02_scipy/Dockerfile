# Add SciPy
FROM cwaldbieser/jupyterhub:v1

# Install OS deps.
RUN apt-get update && apt-get install -y \
    libatlas-dev \
    liblapack-dev \
    gfortran \
    swig

# Install python modules
RUN git clone https://github.com/scipy/scipy.git /srv/scipy
RUN /bin/bash -c 'cd /srv/scipy; git checkout tags/v0.16.1'
RUN /bin/bash -c 'cd /srv/scipy; /root/.virtualenvs/jupyterenv3/bin/python /srv/scipy/setup.py install' 

