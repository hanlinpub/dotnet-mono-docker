FROM mcr.microsoft.com/dotnet/core/runtime:3.1 AS final

LABEL maintainer="jack@hanlin.com.tw"

# https://www.e-iceblue.cn/spiredoc/how-to-use-spire-doc-on-net-core.html
# https://github.com/dotnet/dotnet-docker/issues/618
# Per tech support, install Mono to prevent certain documents from crashing Spire.
RUN apt update \
    && apt install -y apt-transport-https dirmngr gnupg ca-certificates \
	&& apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF

RUN echo "deb https://download.mono-project.com/repo/debian stable-stretch main" | tee /etc/apt/sources.list.d/mono-official-stable.list \
	&& apt update \
	&& apt install -y \
		libc6-dev \
		libgdiplus \
		mono-devel \
	&& rm -rf /var/lib/apt/lists/*
