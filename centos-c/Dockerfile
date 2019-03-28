FROM centos:7

ENV CMAKE_ROOT /usr/local/share/cmake-3.14/
RUN curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.163.com/.help/CentOS7-Base-163.repo
RUN yum clean all; rpm --rebuilddb; \
    yum install -y wget curl which tar sudo openssh-server openssh-clients rsync; \
    yum install -y gcc gcc-c++ make git zsh vim ; \
    sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)" ; exit 0;

RUN wget https://github.com/Kitware/CMake/releases/download/v3.14.0/cmake-3.14.0.tar.gz \
    && tar -xzf cmake-3.14.0.tar.gz && cd cmake-3.14.0 && ./bootstrap && make && make install && cd .. && rm -rf cmake*

CMD ["/bin/zsh"]
