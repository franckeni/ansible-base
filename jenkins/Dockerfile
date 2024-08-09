FROM jenkins/jenkins:2.462.1-jdk21
USER root
RUN apt-get update && apt-get install -y lsb-release
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc \
  https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) \
  signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
  https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli
RUN apt-get install software-properties-common -y
RUN add-apt-repository ppa:deadsnakes/ppa
RUN apt-get -y update && sudo apt-get upgrade -y
RUN apt-get -y install python3.12 python3-pip
RUN pip3 install ansible --upgrade 
USER jenkins
RUN jenkins-plugin-cli --plugins "blueocean docker-workflow"