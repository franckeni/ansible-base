FROM jenkins/jenkins:2.462.1-jdk21
USER root
RUN apt-get update && apt-get install -y lsb-release
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
#RUN chmod 666 /var/run/docker.sock
RUN addgroup docker && usermod -aG docker jenkins
RUN apt-get update && apt-get install -y docker-ce-cli
RUN apt-get update -y && apt-get upgrade -y && apt-get install -y python3 python3-pip sshpass
RUN pip3 install ansible --upgrade --break-system-packages
USER jenkins
RUN jenkins-plugin-cli --plugins "blueocean docker-workflow"