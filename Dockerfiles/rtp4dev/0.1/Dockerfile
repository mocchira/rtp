FROM mocchira/rtp4all:0.1
WORKDIR /grpc
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    apt-transport-https bash-completion \
    gdb strace ltrace valgrind linux-perf-4.4 \
    dstat \
    netcat ngrep tcpdump net-tools && \
# workaround for The "No module named _sysconfigdata_nd"
    ln -s /usr/lib/python2.7/plat-x86_64-linux-gnu/_sysconfigdata_nd.py /usr/lib/python2.7/ && \
# workaround for https://github.com/docker/docker/issues/14140 https://github.com/dotcloud/docker/issues/5490
    mv /usr/sbin/tcpdump /usr/bin/tcpdump && \
    hash -r && \
# install bcc tools
    echo "deb [trusted=yes] https://repo.iovisor.org/apt/xenial xenial-nightly main" | tee /etc/apt/sources.list.d/iovisor.list && \
    apt-get update && \
    apt-get install -y --no-install-recommends bcc-tools && \
    rm -rf /var/lib/apt/lists/*
# path for https://github.com/iovisor/bcc including opensnoop and so on
ENV PATH /usr/share/bcc/tools:$PATH


