FROM mocchira/rtp4dev:0.1

# install pagkages
RUN apt-get update                                                      && \
    apt-get install -y --no-install-recommends                             \
        ncurses-dev libtolua-dev exuberant-ctags                        && \
    ln -s /usr/include/lua5.2/ /usr/include/lua                         && \
    ln -s /usr/lib/x86_64-linux-gnu/liblua5.2.so /usr/lib/liblua.so     && \
    cd /tmp                                                             && \
# build and install vim
    git clone -b v7.4.2367 https://github.com/vim/vim.git               && \
    cd vim                                                              && \
    ./configure --with-features=huge --enable-luainterp                    \
        --enable-gui=no --without-x --prefix=/usr                       && \
    make VIMRUNTIMEDIR=/usr/share/vim/vim74                             && \
    make install                                                        && \
# get go tools
    go get golang.org/x/tools/cmd/benchcmp                              && \
    go get golang.org/x/tools/cmd/callgraph                             && \
    go get golang.org/x/tools/cmd/cover                                 && \
    go get golang.org/x/tools/cmd/digraph                               && \
    go get golang.org/x/tools/cmd/fiximports                            && \
    go get golang.org/x/tools/cmd/godex                                 && \
    go get golang.org/x/tools/cmd/godoc                                 && \
    go get golang.org/x/tools/cmd/goimports                             && \
    go get golang.org/x/tools/cmd/gomvpkg                               && \
    go get golang.org/x/tools/cmd/gorename                              && \
    go get golang.org/x/tools/cmd/gotype                                && \
    go get golang.org/x/tools/cmd/guru                                  && \
    go get golang.org/x/tools/cmd/heapview                              && \
    go get golang.org/x/tools/cmd/oracle                                && \
    go get golang.org/x/tools/cmd/stress                                && \
    go get golang.org/x/tools/cmd/stringer                              && \
    go get github.com/nsf/gocode                                        && \
    go get github.com/rogpeppe/godef                                    && \
    go get github.com/tools/godep                                       && \
    go get github.com/golang/lint/golint                                && \
    go get github.com/kisielk/errcheck                                  && \
    go get github.com/jstemmer/gotags                                   && \
    go get github.com/zmb3/gogetdoc                                     && \
    go get github.com/derekparker/delve/cmd/dlv                         && \
    go get github.com/davecheney/httpstat                               && \
    go get github.com/davecheney/gcvis                                  && \
# cleanup
    apt-get remove -y ncurses-dev                                       && \
    apt-get autoremove -y                                               && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/*

# install vim plugins
RUN mkdir -p ~/.vim/bundle                                              && \
    cd  ~/.vim/bundle                                                   && \
    git clone --depth 1 https://github.com/gmarik/Vundle.vim.git        && \
    git clone --depth 1 https://github.com/fatih/vim-go.git             && \
    git clone --depth 1 https://github.com/majutsushi/tagbar.git        && \
    git clone --depth 1 https://github.com/Shougo/neocomplete.vim.git   && \
    git clone --depth 1 https://github.com/scrooloose/nerdtree.git      && \
    git clone --depth 1 https://github.com/bling/vim-airline.git        && \
    git clone --depth 1 https://github.com/tpope/vim-fugitive.git       && \
    git clone --depth 1 https://github.com/jistr/vim-nerdtree-tabs.git  && \
    git clone --depth 1 https://github.com/mbbill/undotree.git          && \
    git clone --depth 1 https://github.com/Lokaltog/vim-easymotion.git  && \
    git clone --depth 1 https://github.com/scrooloose/nerdcommenter.git && \
# cleanup
    rm -rf Vundle.vim/.git vim-go/.git tagbar/.git neocomplete.vim/.git    \
        nerdtree/.git vim-airline/.git vim-fugitive/.git                   \
        vim-nerdtree-tabs/.git undotree/.git vim-easymotion/.git           \
        nerdcommenter/.git
