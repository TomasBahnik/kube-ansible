FROM python_ssh_root

# Install SSH server
#RUN apt-get update && \
#    apt-get install -y openssh-server && \
#    mkdir /var/run/sshd

# Copy SSH configuration (if needed)
# COPY sshd_config /etc/ssh/sshd_config

# Expose SSH port
EXPOSE 22

# Start SSH service on container startup
CMD ["/usr/sbin/sshd", "-D"]
