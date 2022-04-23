ARG VARIANT="latest"
FROM ghcr.io/openscript/vscode-dev-container-tectonic:${VARIANT}

ARG DEBIAN_FRONTEND=noninteractive
RUN apt update && apt upgrade -y
RUN apt install -y --no-install-recommends python3-pygments biber cmake build-essential

RUN cpan -i App::cpanminus
RUN cpanm YAML::Tiny && cpanm File::HomeDir

RUN git clone https://github.com/cmhughes/latexindent.pl.git

RUN mkdir latexindent.pl/build
WORKDIR "/app/latexindent.pl/build"

RUN cmake ../path-helper-files && make install
