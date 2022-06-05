FROM jenkins/jenkins:2.332.3-lts

# ARG AWS_ACCESS_KEY_ID
# ARG AWS_SECRET_ACCESS_KEY
# ARG AWS_ECR_ADDRESS=<account id>.dkr.ecr.<region>.amazonaws.com

USER root

RUN apt-get update -y -q \
    && apt-get install -y -q --no-install-recommends \
    ca-certificates \
    curl \
    gnupg \
    lsb-release \
    && mkdir -p /etc/apt/keyrings \
    && curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /etc/apt/keyrings/docker.gpg \
    && echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
    $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get update -y -q \
    && apt-get install -y -q --no-install-recommends \
    docker-ce \
    docker-ce-cli \
    containerd.io \
    docker-compose-plugin \
    && usermod -aG docker jenkins \
    && jenkins-plugin-cli --plugins "blueocean:1.25.3 docker-workflow:1.28" \
    && rm -rf /var/lib/apt/lists/*

RUN apt-get update -y -q \
    && apt-get install -y -q --no-install-recommends \
    amazon-ecr-credential-helper \
    unzip \
    && curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip \
    && ./aws/install \
    && apt-get purge unzip -y -q \
    && rm -rf awscliv2.zip \
    && rm -rf /var/lib/apt/lists/*

USER jenkins

RUN mkdir -p ~/.docker \
    && echo echo -e '{\n    "credsStore": "ecr-login"\n}' > ~/.docker/config.json

# RUN aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin ${AWS_ECR_ADDRESS}

COPY --chown=jenkins:jenkins plugins.txt /usr/share/jenkins/ref/plugins.txt

RUN jenkins-plugin-cli -f /usr/share/jenkins/ref/plugins.txt
