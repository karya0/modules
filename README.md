# Building the Modules

## Build Mesos with some unbundled dependencies

### Preparing Mesos source code
First we need to prepare Mesos source code.  You can either download the Mesos
standard release in the form of a tarball and extract it, or clone the git
repository.

Let us assume you did extract/clone
the repo into `~/mesos`. Let us also assume that you build mesos in a subfolder
called `build` (`~/mesos/build`).

### Building and Install Mesos
Next, we need to configure and build Mesos.
Due to the fact that modules will need to have access to a couple of libprocess
dependencies, mesos itself should get built with unbundled dependencies to
reduce chances of problems introduced by varying versions (libmesos vs. module
library).

We recommend using the following configure options:

```
./configure --with-glog=/usr/local --with-protobuf=/usr/local --with-boost=/usr/local
make
make install
```

## Build Mesos-Modules

Once that is done, extract/clone the mesos-modules package. For the sake of this
example, that could be in `~/mesos-modules`. Note that you should not put
`mesos-modules` into the `mesos` folder.

You may now run start building the modules.

The configuration phase needs to know some details about your mesos installation
location, hence the following are used:
`--with-mesos=/path/to/mesos/installation`

## Example
```
./bootstrap
mkdir build && cd build
../configure --with-mesos=/path/to/mesos/installation
make
```

At this point, the Module libraries are ready in `/build/.libs`.
