# Setting up the Pico SDK

If you want to make the installation as simple as possible just follow the steps below (you can simply cut and paste these commands into your terminal):

**Step 1.** Create a new directory in your home directory to keep everything tidily in one place:

```bash
cd ~
mkdir pico
cd pico
```

**Step 2.** Install the Pico SDK and examples:

```bash
git clone -b master https://github.com/raspberrypi/pico-sdk.git
cd pico-sdk
git submodule update --init
cd ..
git clone -b master https://github.com/raspberrypi/pico-examples.git
```

**Step 3.** Install the MicroPython port (optional):

```bash
git clone -b pico https://github.com/raspberrypi/micropython.git
cd micropython
git submodule update --init -- lib/pico-sdk
cd lib/pico-sdk
git submodule update --init
cd ../../..
```

**Step 4.** Install the toolchain needed to build Pico projects.

```bash
sudo apt update
sudo apt install cmake gcc-arm-none-eabi build-essential
```

**Step 5.** Install the Pimoroni Pico libraries:

```bash
git clone https://github.com/pimoroni/pimoroni-pico.git
cd pimoroni-pico
mkdir build
```

And you're done. Everything is installed and ready to go.

A good place to start is to build our examples which will prove that everything is setup correctly. Our project is setup to mimic the approach that Raspberry Pi have taken so if you're familiar with building their examples this should be a familiar process.

```
cd build
cmake ..
make
```

When the `make` command has completed you'll see that a number of new files and directories have appeared in your `build` directory. For the purpose of building our examples the one that matters is the `examples` directory.

Inside `examples` will be one directory per product, each of which contain at least one `.uf2` file that can be flashed directly onto your Pico.
