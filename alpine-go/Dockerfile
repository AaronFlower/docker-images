FROM alpine:3.7

RUN echo http://mirrors.ustc.edu.cn/alpine/v3.7/main/ > /etc/apk/repositories 
RUN apk update
RUN apk add git zsh vim gcc
RUN sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)" ; exit 0;
# install go
RUN wget https://dl.google.com/go/go1.11.2.linux-amd64.tar.gz -O go.tar.gz
RUN tar -C /usr/local -xzf go.tar.gz
RUN rm -rf go.tar.gz

# https://stackoverflow.com/questions/34729748/installed-go-binary-not-found-in-path-on-alpine-linux-docker
ENV PATH $PATH:/usr/local/go/bin
RUN mkdir /lib64 && ln -s /lib/libc.musl-x86_64.so.1 /lib64/ld-linux-x86-64.so.2

# add go workspace
RUN mkdir $HOME/go

# init vim
# RUN git clone https://github.com/AaronFlower/YAV-dotvim.git ~/.vim
# RUN ln -s ~/.vim/vimrc ~/.vimrc
# RUN vim +PlugInstall +qall
# RUN vim +GoInstallBinaries +qall

CMD ["/bin/zsh"]

