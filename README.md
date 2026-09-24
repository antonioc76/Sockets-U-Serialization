# Sockets [U](https://en.wikipedia.org/wiki/Union_(set_theory)) Serialization (SUS)
An implementation agnostic IPC system and specification based on WebSockets and JSON. Developed as the middleware for Sooner Competitive Robotics STORM 2026 codebase.

# Architecture
The communication protocol is described by the following diagram

![Architecture.png](images/architecture.png)

# Running binaries
The simplest way to use SUS is to download and run the relay server from the project releases page.

# Examples
Move to the build directory or the directory containing the downloaded binaries and run

`sudo chmod +x relay_server client1 client2` (1st time only)

`./relay_server`

as another process run

`./client1`

and another run

`./client2`

client2 should print the message that it receives from client1

`heard: {"ID":200,"message":"Hello Client2!"}`

and client1 should print the message that it receives from client2

`heard: {"ID":99,"message":"Hello Client1!"}`

If you are using C++, you can follow the example files [here](/ws_server/src/) for creating a node with a libhv client. 

# Building from source
Installation instructions for the dependency `libhv` – which was used to write the relay server and example clients – are included here.

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
3. Ensure you have G++-13 installed (for C++ 20)

if the major version number of 

`g++ --version` 

is 13 or higher, continue to the next section.

Install g++-13: 

```
sudo apt update 
sudo apt install -y software-properties-common 

sudo add-apt-repository ppa:ubuntu-toolchain-r/test 
sudo apt update 

sudo apt install -y gcc-13 g++-13
```

## Build project
4. Build relay server and examples from source

```
cd Sockets-U-Serialization
cmake -S ./ws_server -B ./build -DCMAKE_CXX_COMPILER=g++-13
cmake --build ./build
```