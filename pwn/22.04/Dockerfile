FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ Asia/Seoul
ENV PYTHONIOENCODING UTF-8
ENV LC_CTYPE C.UTF-8
ENV TERM=xterm-256color

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone
RUN dpkg --add-architecture i386
RUN sed -i 's/archive.ubuntu.com/mirror.kakao.com/g' /etc/apt/sources.list && rm -rf /var/lib/apt/lists/*

WORKDIR /root

RUN apt update -y
RUN apt upgrade -y
RUN apt install libc6:i386 -y
RUN apt update -y
RUN apt install python3 python3-pip python3-dev python3-setuptools libssl-dev  -y
RUN apt install libffi-dev build-essential libc6-dbg gcc-multilib make gcc netcat git curl -y
RUN apt install wget gdb zsh ruby-full ssh libffi-dev libc6-i386 software-properties-common -y
RUN add-apt-repository ppa:jonathonf/vim -y
RUN apt install vim -y
RUN apt install fonts-powerline file gem -y

RUN wget https://bootstrap.pypa.io/get-pip.py && python3 get-pip.py && rm get-pip.py

RUN python3 -m pip install --upgrade pip
RUN pip3 install unicorn filebytes keystone-engine pwntools requests z3-solver capstone ROPgadget ropper angr # buildkit
RUN apt install libcapstone-dev -y

RUN apt install ruby-full ruby-dev -y
RUn apt install checksec -y
RUN gem install one_gadget

RUN apt update
# FOR vim
RUN apt install nodejs npm tmux -y
RUN npm install -g n
RUN n latest


RUN echo "dd"

RUN git clone https://github.com/h1ghl1kh7/tools.git /root/.docker_set
WORKDIR /root/.docker_set/ubuntu
RUN ./zsh-plugin.sh
WORKDIR /root/.docker_set/gef
RUN ./gef_setting.sh

WORKDIR /root/

RUN vim +PlugInstall +qall

# additional install
RUN apt update -y
RUN apt install gdbserver -y
RUN apt install clangd -y
RUN apt install universal-ctags -y

RUN apt install python3-venv -y
RUN pip3 install jedi-language-server
RUN pip3 install jedi

RUN vim +"CocInstall -sync coc-json coc-pyright coc-clangd coc-docker coc-jedi coc-tsserver coc-html coc-prettier coc-css coc-yaml coc-highlight coc-angular coc-snippets" +qall


ENTRYPOINT [ "zsh" ]
