FROM ubuntu
RUN apt update
RUN apt install curl tar wget clang pkg-config libssl-dev jq build-essential git make ncdu -y
RUN export ver="1.19.1" && wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz" && rm -rf /usr/local/go && tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz" && rm "go$ver.linux-amd64.tar.gz"
RUN echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile &&  source $HOME/.bash_profile
RUN rm -rf celestia-node && git clone https://github.com/celestiaorg/celestia-node.git && cd celestia-node/ && git checkout tags/v0.4.2 && make install

