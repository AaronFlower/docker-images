FROM alpine:3.9

RUN echo http://mirrors.ustc.edu.cn/alpine/v3.9/main/ > /etc/apk/repositories
RUN apk update && apk add gcc g++ && apk add make cmake valgrind && apk add git zsh vim && sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)" ; exit 0;

CMD ["/bin/zsh"]
