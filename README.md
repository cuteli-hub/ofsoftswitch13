# ofsoftswitch13

This is a modified version of ofsoftswitch, which is included two new OFPMatch fields: tcp_ack_diff and tcp_seq_diff.
This specific version is used to facilitate the tcp connection hand off between different ends. So, the two added fields are used to
synchronize the ack and seq number in the TCP header between different ends.



# Install:

Finally you must install the ofsoftswitch tool. This tool is similar to Open vSwitch, not as powerful as Open vSwitch but unlike OVS, this tool is capable of implement Flow Meters into virtual switches. So follow these steps:

Install required libraries:

sudo apt-get install -y git-core autoconf automake autotools-dev pkg-config \

     make gcc g++ libtool libc6-dev cmake libpcap-dev libxerces-c2-dev \
     unzip libpcre3-dev flex bison libboost-dev

Downgrade "GNU Bison" library to compile correctly NetBee

wget -nc http://de.archive.ubuntu.com/ubuntu/pool/main/b/bison/bison_2.5.dfsg-2.1_amd64.deb \
         http://de.archive.ubuntu.com/ubuntu/pool/main/b/bison/libbison-dev_2.5.dfsg-2.1_amd64.deb

sudo dpkg -i bison_2.5.dfsg-2.1_amd64.deb libbison-dev_2.5.dfsg-2.1_amd64.deb
rm bison_2.5.dfsg-2.1_amd64.deb libbison-dev_2.5.dfsg-2.1_amd64.deb

Install "NetBee"

wget -nc http://www.nbee.org/download/nbeesrc-jan-10-2013.zip
unzip nbeesrc-jan-10-2013.zip
cd nbeesrc-jan-10-2013/src
cmake .
make
sudo cp ../bin/libn*.so /usr/local/lib
sudo ldconfig
sudo cp -R ../include/* /usr/include/
cd ../..

Install ofsoftswitch:

git clone https://github.com/CPqD/ofsoftswitch13.git
cd ofsoftswitch13
./boot.sh
./configure
make
sudo make install


# Contact
E-mail: Wenjun Fan (efan at dit.upm.es)
