FROM jenkins/ssh-agent:jdk11
USER root
RUN apt-get update && apt-get install -y lsb-release ca-certificates curl unzip && update-ca-certificates
RUN curl -fsSLo /usr/share/keyrings/docker-archive-keyring.asc https://download.docker.com/linux/debian/gpg
RUN echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.asc] \
https://download.docker.com/linux/debian $(lsb_release -cs) stable" > /etc/apt/sources.list.d/docker.list
RUN apt-get update && apt-get install -y docker-ce-cli
WORKDIR /opt
RUN curl -LO https://dl.k8s.io/release/v1.25.0/bin/linux/amd64/kubectl && install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
RUN curl -O https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.zip \
&& unzip apache-maven-3.8.6-bin.zip && chmod -R 755 /opt/apache-maven-3.8.6/bin && rm apache-maven-3.8.6-bin.zip
ENV PATH=$PATH:/opt/apache-maven-3.8.6/bin
RUN echo "PATH=${PATH}" >> /etc/environment