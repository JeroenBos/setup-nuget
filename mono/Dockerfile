FROM ubuntu:22.04

# install mono
RUN apt update
RUN apt install ca-certificates gnupg wget -y
RUN gpg --homedir /tmp --no-default-keyring --keyring /usr/share/keyrings/mono-official-archive-keyring.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF
RUN "deb [signed-by=/usr/share/keyrings/mono-official-archive-keyring.gpg] https://download.mono-project.com/repo/ubuntu stable-focal main" | tee /etc/apt/sources.list.d/mono-official-stable.list
RUN apt update
RUN DEBIAN_FRONTEND=noninteractive apt install mono-xsp4 -y

# install nuget
WORKDIR /app
ENV exe_path /app/nuget.exe
RUN wget --no-verbose https://dist.nuget.org/win-x86-commandline/latest/nuget.exe -O "$exe_path" && chmod +rx "$exe_path"
RUN printf "#!/bin/bash\n mono '$exe_path' \$@" > '/usr/bin/nuget' && chmod +x /usr/bin/nuget
