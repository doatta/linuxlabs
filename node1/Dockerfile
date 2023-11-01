# syntax=docker/dockerfile:1

FROM almalinux:latest
ENV user=jupyter

# Install ssh server
RUN dnf install openssh-server sudo -y

# Configure systemd
RUN rm -f /lib/systemd/system/multi-user.target.wants/*;\
rm -f /etc/systemd/system/*.wants/*;\
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*;\
rm -f /lib/systemd/system/anaconda.target.wants/*;

# Configure SSH
RUN systemctl enable sshd
# Copy keys from labs-jupyter docker image
COPY --from=labs-jupyter /home/$user/.ssh/id_ed25519.pub /root/.ssh/authorized_keys
RUN chown root:root /root/.ssh/authorized_keys
RUN rm -rf /run/nologin

# Run systemd
CMD /lib/systemd/systemd --system --unit=multi-user.target

EXPOSE 22