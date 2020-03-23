# CMake

**iRODS** and associated software (iCommands, plugins, etc) use the build system `cmake`
for futureproofing and portability.

## Intro and Tutorial

  - [Hello world](
    http://derekmolloy.ie/hello-world-introductions-to-cmake/#Example_1_The_Hello_World_Example )
  - [Github files](https://github.com/derekmolloy/exploringBB/tree/master/extras/cmake
)

## usage to compile the default (master) branch of the iRODS server

The following steps allow compiling iRODS from source code (with debug symbols intact) and installing a single-node ICAT server appropriate for simple debugging, training and demonstration purposes:

  1. make sure `g++` package is installed and we're logged in as a sudo-enabled user.
  (Also want irods-externals installed; enable `coredev` repo (see :
    http://packages.irods.org)

  1. use git to make a local iRODS repo
    ```
    $ mkdir ~/github ; cd ~/github
    $ git clone http://github.com/irods/irods
    $ (cd irods ; git submodule update --init)
    $ git clone http://github.com/irods/irods_client_icommands
    ```
  1. make build directories in parallel with these:
    ```
    cd ~/github ; for x in  $dir; do mkdir build__$x; done
    ```
  1. generate a CMake build configuration for iRODS
    ```
    $ cd ~/github/build__irods
    $ cmake -G'Unix Makefiles' \
          -D'CMAKE_BUILD_TYPE=Debug' -D'CMAKE_VERBOSE_MAKEFILE=True. \
          ../irods
    $ make -j3 package
    $ sudo dpkg -i irods-dev*.deb irods-runtime*.deb
    ```
    This:
      * Sets up for a `Debug` rather than default `Release` compilation
        (appropriate for use with `valgrind`,`gdb`,`rr`).
      * increases the build verbosity such that each command line is echoed to the screen.
      * Assumes we will be using `make` and assumes a moderate parallelism for the build machine.
        For a `ninja`-powered build (and appropriate usage of the build machines full parallelism, make sure
        and invoke `cmake` with `-G Ninja`.

  1. type `make package` to generate debian/Ubuntu packages for development, server, and runtime, and database plugins

  1. type `dpkg -i irods-dev*.deb irods-runtime*.deb`

  1. build the `icommands` command-line client executables (needed for installation and setup of the iRODS server)
  ```
  $ cd ../build__irods_irods_client_icommands
  $ cmake ../irods_client_icommands
  $ make package
  $ sudo dpkg -i *icommands*.deb
  ```
  1. install the remainder of the packages in `~/github/build__irods`. If we're running a machine-local ICAT using PostgreSQL:
  ```
  $ cd ../build__irods
  $ sudo dpkg -i irods*database*postgres*.deb \
    irods-server*.deb
  ```
  1. a console message will advise how to set up irods. Since we're just setting up a single-node system, we'll just do as prescribed
