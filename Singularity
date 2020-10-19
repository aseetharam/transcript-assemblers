Bootstrap: docker
From: ubuntu:20.04


%labels
   MAINTAINER Arun Seetharam
   EMAIL arnstrm@iastate.edu

%environment
   export TRINITY_HOME=/usr/local/bin/trinityrnaseq
   export PATH=$PATH:/usr/local/bin/trinityrnaseq:/usr/local/bin/trinityrnaseq/util
   
%post
   apt-get update
   apt-get install -y build-essential wget curl git autoconf automake
   apt-get install -y gcc g++ bison make cmake
   apt-get install -y perl zlib1g-dev libbz2-dev liblzma-dev libcurl4-gnutls-dev libssl-dev libncurses5-dev liblpsolve55-dev libboost-all-dev rsync librsync-dev 
   # strawberry
   cd /root
   git clone https://github.com/ruolin/strawberry.git
   cd strawberry && \
      sh cmake.sh && \
      cd build && \
      make && \
      make install
   # install class2
   cd /root
   wget https://downloads.sourceforge.net/project/splicebox/CLASS-2.1.7.tar.gz
   tar -xf CLASS-2.1.7.tar.gz
   cd CLASS-2.1.7
   sh build.sh
   mv class junc clnb grader addXS /usr/bin/
   # instll stringtie
   cd /root
   git clone https://github.com/gpertea/stringtie
   cd stringtie
   make release
   mv stringtie /usr/bin/
   # install cufflinks
   apt-get install -y cufflinks
   # trinity
   cd /root
   git clone --recursive https://github.com/trinityrnaseq/trinityrnaseq.git  
   cd trinityrnaseq
   make && \
   make plugins && \
   make install
   # required programs
   apt-get install -y bowtie2 jellyfish salmon
