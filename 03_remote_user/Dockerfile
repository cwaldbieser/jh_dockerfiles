# Build a Jupyterhub with matplotlib v1.4.
FROM cwaldbieser/jupyterhub:v2

# Copy config file.
COPY jupyterhub_config.py /srv/jupyterhub/

# Install python modules
RUN git clone https://github.com/cwaldbieser/jhub_remote_user_authenticator.git /srv/jh_remote_user
# SET PYTHONPATH
ENV PYTHONPATH=/srv/jh_remote_user

