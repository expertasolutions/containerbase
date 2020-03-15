FROM mcr.microsoft.com/powershell:latest AS build
RUN apt-get update -y && apt-get install -y \
    --allow-downgrades --allow-remove-essential --allow-change-held-packages \
    python
RUN apt-get install -y ca-certificates curl apt-transport-https lsb-release gnupg
RUN curl -sL https://packages.microsoft.com/keys/microsoft.asc | \
    gpg --dearmor | \
    tee /etc/apt/trusted.gpg.d/microsoft.asc.gpg > /dev/null
RUN export AZ_REPO=$(lsb_release -cs) && \
    echo $AZ_REPO && \
    echo "deb [arch=amd64] https://packages.microsoft.com/repos/azure-cli/ $AZ_REPO main" | \
    tee /etc/apt/sources.list.d/azure-cli.list
RUN apt-get update -y && apt-get install azure-cli -y