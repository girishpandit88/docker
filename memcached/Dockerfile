FROM ubuntu

# Update the default application repository sources list
RUN apt-get update \
  && apt-get install -y memcached

# Port to expose (default: 11211)
EXPOSE 11211

# Default Memcached run command arguments
# Change to limit memory when creating container in Tutum 
CMD ["-m", "64"]

# Set the user to run Memcached daemon
USER daemon

# Set the entrypoint to memcached binary
ENTRYPOINT memcached