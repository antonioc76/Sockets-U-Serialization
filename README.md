Dependencies

The communications specification is based on WebSockets and json and is implementation agnostic, but the dependencies for using libhv – which was used to write the Relay Server and example clients – is included here.

Download libhv: https://github.com/ithewei/libhv

Navigate to your local libhv folder and run

mkdir build && cd build
cmake ..
make -j$(nproc)
sudo make install

Using libhv in your node

If you are using cmake, you can follow the example files here in /src for creating a node with a libhv client. 
