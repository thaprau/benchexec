# P4 Extension for Benchexec

## Installation


### Dependencies

#### Docker Engine
To install docker, follow the instruction on [dockers website](https://docs.docker.com/engine/install/)

Also install the extension for docker to be excecuted through python:

```
sudo pip3 install docker
```

### Benchexec installation

To install benchexecute with p4 extensions follow these steps. First clone the repository, switch to correct
branch and install the application:

```
git clone https://github.com/thaprau/benchexec.git
cd benchexec
git checkout bench_p4
pip3 install .
```

### Docker file setup
To setup the required docker files, some images has to be created locally. In total, three images has to be built.
1. Node image - basic image which acts as a node in the network
2. Switch image - Image that runs the bmv2 software provided by the p4 institution
3. Ptf tester image - Image that runs PTF(package test framwork) also provided by p4 institution

To build the images, run the following commands or use the setup script provided in `/docker_files`.

```
sudo docker build -t basic_node basic_node
sudo docker build -t switch_bmv2 switch_bmv2
sudo docker build -t ptf_tester ptf_tester
```
or use the installation script(not added yet)

```
sudo docker_install.sh
```

## Execution

To run benchexec with p4 extension. Run benchexec normally, but with tag -p4 true. An example would be:
```
sudo benchexec -p4 true doc/johanP4Test.XML
```