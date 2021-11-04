#todo this needs more deets

https://github.com/pykaldi/pykaldi

Installing Kaldi, Speed Machine Learning package

note:
1) Kaldi uses C++. Therefore, install both C++ Kaldi, and Python binding pykaldi.
2) This has many dependencies..
3) ignore "conda install -c pykaldi pykaldi". We gonna install from source.

Installation steps:
1) set up virtual env and activate

2) download git repository

git clone https://github.com/pykaldi/pykaldi.git
cd pykaldi

3) install dependencies

# Ubuntu
sudo apt-get install autoconf automake cmake curl g++ git graphviz \
    libatlas3-base libtool make pkg-config subversion unzip wget zlib1g-dev

pip install --upgrade pip
pip install --upgrade setuptools
pip install numpy pyparsing
pip install ninja  # not required but strongly recommended

4) install Google Protobuf

ref: https://github.com/protocolbuffers/protobuf/blob/master/src/README.md

git clone https://github.com/protocolbuffers/protobuf.git
cd protobuf
git submodule update --init --recursive
./autogen.sh

./configure
make
make check
sudo make install
sudo ldconfig # refresh shared library cache.

5) install CLIF (C++ Language Interface Foundation)