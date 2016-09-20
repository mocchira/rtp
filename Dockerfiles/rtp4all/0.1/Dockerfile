FROM mocchira/rtp4lang:0.1
WORKDIR /grpc
RUN git clone -b v1.0.0 https://github.com/grpc/grpc \
    && git clone -b v1.0.1 https://github.com/grpc/grpc-java \
    && pip install grpcio grpcio-tools \
    && gem install grpc grpc-tools \
    && go get google.golang.org/grpc \
    && go get -u github.com/golang/protobuf/proto \
    && go get -u github.com/golang/protobuf/protoc-gen-go
