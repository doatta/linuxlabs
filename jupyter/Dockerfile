# syntax=docker/dockerfile:1

FROM almalinux:latest
ENV user=jupyter

# Install jupyter labs and ssh client
RUN dnf install python3 python3-pip openssh-clients -y
RUN pip install jupyterlab sshkernel
RUN python3 -m sshkernel install 

# Create user
RUN useradd -m $user -u 1000
USER $user

# Configure SSH
RUN mkdir -p /home/$user/.ssh
RUN ssh-keygen -m PEM -t ed25519 -f /home/$user/.ssh/id_ed25519 -q -N ''

# Copy tasks
COPY --chown=$user tasks /home/$user/tasks

# Run jupyter
CMD jupyter lab --notebook-dir /home/$user/tasks --no-browser --ip=0.0.0.0

EXPOSE 8888