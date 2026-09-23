# Sockets [U](https://en.wikipedia.org/wiki/Union_(set_theory)) Serialization (SUS)

An implementation agnostic IPC communications system and specification based on WebSockets and JSON.

# Architecture

The communication protocol is described by the following diagram

![Architecture.png](images/architecture.png)

# Building

Installation instructions for the dependency `libhv` – which was used to write the Relay Server and example clients – is included here.

## Dependency

1. Download libhv: https://github.com/ithewei/libhv

2. Install libhv:

```
cd libhv
mkdir build && cd build
cmake ..
make -j$(nproc)
sudo make install
```

## Compiler version
5. Ensure you have G++-13 installed (for C++ 20)

if the major version number of `g++ --version` is 13 or higher, continue to the next section

```
cd ~
sudo apt update 
sudo apt install -y software-properties-common 

sudo add-apt-repository ppa:ubuntu-toolchain-r/test 
sudo apt update 

sudo apt install -y gcc-13 g++-13
```

## Build project
6. Build relay server and examples from source

```
cd Sockets-U-Serialization
cmake -S ./ws_server -B ./build -DCMAKE_C_COMPILER=gcc-13 -DCMAKE_CXX_COMPILER=g++-13
cmake --build ./build
```

# Examples
If you are using C++, you can follow the example files [here](/ws_server/src/) for creating a node with a libhv client. 

in one thread run

`./build/relay_server`

in another run

`./build/client1`

and another run

`./build/client2`

client2 should print the message that it receives from client1

`heard: {"ID":200,"message":"Hello Client2!"}`