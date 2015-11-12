# Build a Jupyterhub with matplotlib v1.4.
FROM cwaldbieser/jupyterhub:v2

# Copy config file.
COPY jupyterhub_config.py /srv/jupyterhub/

# Copy jupyterhub patch.
COPY app.py /usr/local/lib/python3.4/dist-packages/jupyterhub/

# Install python modules
RUN git clone https://github.com/cwaldbieser/jhub_remote_user_authenticator.git /srv/jh_remote_user
# SET PYTHONPATH
ENV PYTHONPATH=/srv/jh_remote_user

