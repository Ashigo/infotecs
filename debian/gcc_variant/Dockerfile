FROM debian:9

ENV dir=openssl

# Update aptitude with new repo
RUN apt-get update

# Install software 
RUN apt-get install -y gcc git perl make build-essential

RUN git clone https://github.com/openssl/openssl.git
WORKDIR ${dir}
RUN ls -la
RUN git checkout -b OpenSSL_1_1_1-stable origin/OpenSSL_1_1_1-stable
RUN ./config > /output.txt && make >> /output.txt && make test >> /output.txt

CMD ["/bin/bash"]