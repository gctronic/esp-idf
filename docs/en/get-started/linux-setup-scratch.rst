**********************************
Setup Linux Toolchain from Scratch
**********************************

.. note::
   This is documentation for the CMake-based build system which is currently in preview release. The documentation may have gaps, and you may encounter bugs (please report either of these). To view documentation for the older GNU Make based build system, switch versions to the 'latest' master branch or a stable release.

The following instructions are alternative to downloading binary toolchain from Espressif website. To quickly setup the binary toolchain, instead of compiling it yourself, backup and proceed to section :doc:`linux-setup`.


Install Prerequisites
=====================

To compile with ESP-IDF you need to get the following packages:

- CentOS 7::

    sudo yum install git wget ncurses-devel flex bison gperf python pyserial cmake ninja-build ccache

- Ubuntu and Debian::

    sudo apt-get install git wget libncurses-dev flex bison gperf python python-serial cmake ninja-build ccache

- Arch::

    sudo pacman -S --needed gcc git make ncurses flex bison gperf python2-pyserial cmake ninja ccache

.. note::
    CMake version 3.5 or newer is required for use with ESP-IDF. Older Linux distributions may require updating, or enabling of a "backports" repository, or installing of a "cmake3" package not "cmake")

Compile the Toolchain from Source
=================================

- Install dependencies:

  - CentOS 7::

        sudo yum install gawk gperf grep gettext ncurses-devel python python-devel automake bison flex texinfo help2man libtool make

  - Ubuntu pre-16.04::

        sudo apt-get install gawk gperf grep gettext libncurses-dev python python-dev automake bison flex texinfo help2man libtool make

  - Ubuntu 16.04::

        sudo apt-get install gawk gperf grep gettext python python-dev automake bison flex texinfo help2man libtool libtool-bin make

  - Debian 9::

        sudo apt-get install gawk gperf grep gettext libncurses-dev python python-dev automake bison flex texinfo help2man libtool libtool-bin make

  - Arch::

        TODO

Download ``crosstool-NG`` and build it::

    cd ~/esp
    git clone -b xtensa-1.22.x https://github.com/espressif/crosstool-NG.git
    cd crosstool-NG
    ./bootstrap && ./configure --enable-local && make install

Build the toolchain::

    ./ct-ng xtensa-esp32-elf
    ./ct-ng build
    chmod -R u+w builds/xtensa-esp32-elf

Toolchain will be built in ``~/esp/crosstool-NG/builds/xtensa-esp32-elf``. Follow :ref:`instructions for standard setup <setup-linux-toolchain-add-it-to-path>` to add the toolchain to your ``PATH``.


Next Steps
==========

To carry on with development environment setup, proceed to section :ref:`get-started-get-esp-idf`.
