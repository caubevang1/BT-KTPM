FROM ubuntu:20.04

# Cài SSH server + sudo + tiện ích cơ bản
RUN apt-get update && apt-get install -y \
    openssh-server \
    sudo \
    && rm -rf /var/lib/apt/lists/*

# Tạo user 
RUN useradd -ms /bin/bash docker && echo "docker:docker" | chpasswd && adduser docker sudo

# Chuẩn bị SSH
RUN mkdir /var/run/sshd

# Cho phép login bằng password
RUN sed -i 's/#PasswordAuthentication yes/PasswordAuthentication yes/' /etc/ssh/sshd_config

# Expose cổng SSH
EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]

