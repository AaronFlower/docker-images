FROM alpine:3.7

RUN echo http://mirrors.ustc.edu.cn/alpine/v3.7/main/ > /etc/apk/repositories 
RUN apk update
RUN apk add gcc g++ 
RUN apk add make cmake valgrind
RUN apk add git zsh vim
RUN sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)" ; exit 0;

CMD ["/bin/zsh"]

