# Use Alpine Linux as base image
FROM alpine:latest

# Install vsftpd
RUN apk update && \
    apk add vsftpd

# Create FTP user and set password
RUN adduser -D -h /home/ftpuser -s /bin/false ftpuser && \
        echo "ftpuser:password" | chpasswd

# Create directory for FTP files and set permissions
RUN mkdir -p /home/ftpuser/ftpfiles && \
    chown -R ftpuser:ftpuser /home/ftpuser/ftpfiles

# Copy vsftpd configuration file
COPY vsftpd.conf /etc/vsftpd/vsftpd.conf

# Create the secure chroot directory
RUN mkdir -p /var/run/vsftpd/empty

# Expose FTP port
EXPOSE 8021
EXPOSE 40000-50001

# Mount volume to /home/ftpuser/ftpfiles
VOLUME ["/home/ftpuser/ftpfiles"]

# Start vsftpd
CMD ["/usr/sbin/vsftpd", "/etc/vsftpd/vsftpd.conf"]
