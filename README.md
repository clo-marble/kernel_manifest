# Paranoid Android GKI

## Setting up your machine ##

You must be running a 64-bit Linux distribution and must have installed some packages to build
Paranoid Android. Google recommends using [Ubuntu](http://www.ubuntu.com/download/desktop) for
this and provides instructions for setting up the system (with Ubuntu-specific commands) on
[the Android Open Source Project website](https://source.android.com/source/initializing.html#setting-up-a-linux-build-environment).

Once you have set up your machine according to the instructions by Google, return here and carry
on with the rest of the instructions.

## Grabbing the source ##

[Repo](http://source.android.com/source/developing.html) is a tool provided by Google that
simplifies using [Git](http://git-scm.com/book) in the context of the Android source.

### Installing Repo ###

```bash
# Make a directory where Repo will be stored and add it to the path
$ mkdir ~/.bin
$ PATH=~/.bin:$PATH

# Download Repo itself
$ curl https://storage.googleapis.com/git-repo-downloads/repo > ~/.bin/repo

# Make Repo executable
$ chmod a+x ~/.bin/repo
```

# Kernel Build

## Setup

```bash
mkdir WORKSPACE
cd WORKSPACE
```

## Initialize

```bash
repo init -u https://github.com/clo-marble/kernel_manifest.git -b calcite
```

## Sync

```bash
repo sync -c --force-sync --no-clone-bundle --no-tags -j$(nproc --all)
```

## Building

```bash
# Go to the root of the source tree...
cd WORKSPACE

# Run the builder tool.
./build.sh
# Optional arguments:
# -f : Full LTO (longer build time, generates slightly more optimized kernel image)
# -c : Clean build (remove leftover from previous builds)
```
