FROM centos:7

ENV CMAKE_ROOT /usr/local/share/cmake-3.14/
RUN curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.163.com/.help/CentOS7-Base-163.repo
RUN yum clean all; rpm --rebuilddb; \
    yum install -y epel-release; \
    yum install -y wget curl which tar sudo openssh-server openssh-clients rsync; \
    yum install -y gcc gcc-c++ make git zsh ; \
    yum install -y the_silver_searcher; \
    yum install -y ctags-etags; \
    yum install -y ncurses-devel ruby ruby-devel lua lua-devel luajit luajit-devel python python-devel python36 python36-devel python36-setuptools;\
    yum install -y tcl-devel perl perl-devel perl-ExtUtils-ParseXS perl-ExtUtils-XSpp perl-ExtUtils-CBuilder perl-ExtUtils-Embed;\
    yum install -y cscope gtk3-devel libSM-devel libXt-devel libXpm-devel libappstream-glib libacl-devel gpm-devel;\
    easy_install-3.6 pip;\
    sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)" ; exit 0;

RUN rpm -e --nodeps vim-minimal;
# RUN ln -s /usr/bin/python3.6 python3;
RUN git clone https://github.com/vim/vim.git;
RUN cd vim && ./configure --with-features=huge \
 --enable-pythoninterp=yes \
 --enable-python3interp=yes \
 --enable-perlinterp=yes \
 --disable-tclinterp \
 --with-x=yes \
 --enable-gui=gtk3 --enable-multibyte \
 --enable-cscope \
 --with-tlib=ncurses \
--enable-fail-if-missing \
--disable-darwin --enable-luainterp=yes \
--enable-rubyinterp=yes --enable-terminal \
 --enable-fontset --with-luajit --with-python3-command=python3.6 \
--enable-gtk3-check && make && make install && cd .. && rm -rf vim;

RUN git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf && ~/.fzf/install
RUN wget https://github.com/Kitware/CMake/releases/download/v3.14.0/cmake-3.14.0.tar.gz \
    && tar -xzf cmake-3.14.0.tar.gz && cd cmake-3.14.0 && ./bootstrap && make && make install && cd .. && rm -rf cmake*

RUN wget https://dl.google.com/go/go1.12.2.linux-amd64.tar.gz -O go.tar.gz && tar -C /usr/local -xzf go.tar.gz && rm -rf go.tar.gz  && mkdir $HOME/go
ENV PATH $PATH:/usr/local/go/bin
RUN ctags -I __THROW -I __attribute_pure__ -I __nonnull -I __attribute__ --file-scope=yes --langmap=c:+.h --languages=c,c++ --links=yes --c-kinds=+p --c++-kinds=+p --fields=+iaS --extra=+q -R -f ~/systags /usr/include /usr/local/include && pip install --user pynvim;
RUN echo "update66: " && git clone https://github.com/AaronFlower/YAV-dotvim.git ~/.vim && ln -s ~/.vim/vimrc ~/.vimrc
RUN vim +'silent :PlugInstall' +qall
# RUN echo "update33:" && mkdir -p ~/.vim/plugged/YouCompleteMe/third_party/ycmd/clang_archives && cd $_ && \
    # wget https://dl.bintray.com/micbou/libclang/libclang-7.0.0-x86_64-unknown-linux-gnu.tar.bz2;
# RUN vim +'silent :GoInstallBinaries' +qall
# RUN cd ~/.vim/plugged/YouCompleteMe && python3 install.py --clang-completer --go-completer
RUN cd ~/.vim/plugged/YouCompleteMe && git submodule update --init --recursive
RUN echo "update55:" && mkdir -p ~/.vim/plugged/YouCompleteMe/third_party/ycmd/clang_archives;
COPY libclang-7.0.0-x86_64-unknown-linux-gnu.tar.bz2 /root/.vim/plugged/YouCompleteMe/third_party/ycmd/clang_archives/
RUN cd ~/.vim/plugged/YouCompleteMe && python3 install.py --clang-completer
RUN yum install -y valgrind tmux && cd ~ && git clone https://github.com/gpakosz/.tmux.git && git clone https://github.com/AaronFlower/dotfiles.git && ln -s -f ~/dotfiles/tmux.conf.local ~/.tmux.conf.local && gem install rouge

RUN sed -i '/tsflags=nodocs/d' /etc/yum.conf && yum install -y man-pages man-db man

CMD ["/bin/zsh"]
