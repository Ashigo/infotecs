FROM debian:9

ENV dir=openssl

# Add LLVM repo to debian
RUN apt-get update
RUN apt-get install -y wget sudo gnupg git perl apt-transport-https ca-certificates build-essential
RUN echo "deb http://apt.llvm.org/stretch/ llvm-toolchain-stretch-14 main" >> /etc/apt/sources.list
RUN echo "deb-src http://apt.llvm.org/stretch/ llvm-toolchain-stretch-14 main" >> /etc/apt/sources.list
RUN wget -O - https://apt.llvm.org/llvm-snapshot.gpg.key|sudo apt-key add -


# Update aptitude with new repo
RUN apt-get update

# Install software 
RUN apt-get install -y clang-14 lldb-14 lld-14

RUN git clone https://github.com/openssl/openssl.git
WORKDIR ${dir}
RUN ls -la
RUN git checkout -b OpenSSL_1_1_1-stable origin/OpenSSL_1_1_1-stable
RUN export CC=clang-14 && export CXX=clang++-14 && ./config > /output.txt 
RUN make >> /output.txt && make test >> /output.txt

CMD ["/bin/bash"]