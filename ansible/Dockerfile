FROM python_ssh_root

# Install SSH server
#RUN apt-get update && \
#    apt-get install -y openssh-server && \
#    mkdir /var/run/sshd

# Copy SSH configuration (if needed)
# COPY sshd_config /etc/ssh/sshd_config

# The EXPOSE instruction in a Dockerfile serves as a form of documentation,
# indicating which ports the container is expected to listen on.
# However, it does not actually publish the ports.
EXPOSE 22

# Start SSH service on container startup
# -D option
# Runs in the foreground  container won't exit
# Debug mode - Instead of logging to a file or syslog, sshd sends all
# logging and debugging information to the standard error (stderr).
CMD ["/usr/sbin/sshd", "-D"]
