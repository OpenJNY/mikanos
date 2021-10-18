# OpenJNY/mikanos

## Build MikanLoaderPkg by EDK II

```bash
cd $HOME/edk2
# ln -s $HOME/workspace/mikanos/MikanLoaderPkg ./
ln -s /workspaces/mikanos/MikanLoaderPkg ./
source edksetup.sh

vim Conf/target.txt
# ACTIVE_PLATFORM = MikanLoaderPkg/MikanLoaderPkg.dsc
# TARGET = DEBUG
# TARGET_ARCH = X64
# TOOL_CHAIN_TAG = CLANG38

build

# confirm the artifacts
ls -l Build/MikanLoaderX64/DEBUG_CLANG38/X64/Loader.efi
```

## Build kernel

```bash
cd /workspace/mikanos/kernel
./build
```

## Test

While launching `vcxsrv` on windows 10, execute the following command:

```bash
$HOME/osbook/devenv/run_qemu.sh $HOME/edk2/Build/MikanLoaderX64/DEBUG_CLANG38/X64/Loader.efi /workspaces/mikanos/kernel/kernel.elf 
```