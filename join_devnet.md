# TweedleDev 207 - Spacemesh 0.2 Preview Devnet

Release date: October 6th, 2021.

- [Devnet 207 Dashboard](https://dash.spacemesh.io)

- [Devnet 207 Explorer](https://explorer.spacemesh.io)

> This early Spacemesh 0.2 devnet is intended for users who are comfortable using the command line and terminal applications.

---

Follow the instructions below to join the devnet.

## System Requirements

- A computer with a modern Intel, an AMD CPU (2 cores / 4 native threads) or an Apple M1 CPU.
- Windows 10 Home or Pro, macOS, Ubuntu 18.04, Fedora 21, or Debian 8.
- 4 GB RAM.
- 250 GiB free disk space (HDD or SSD).
- An always-on, un-metered Internet connection capable of 10 mbps download and 1 mbps upload.
- Recommended but not required: A graphics card supporting CUDA (minimum compute compatibility 5.0, maximum compute compatibility 8.6), or Vulkan compute API 1.2 or later.

## Installing & Running

1. Download the devnet release zip file for your platform.

- [Windows](https://storage.googleapis.com/go-spacemesh-release-builds/v0.2.3-beta.0/Windows.zip)
- [macOS](https://storage.googleapis.com/go-spacemesh-release-builds/v0.2.3-beta.0/macOS.zip)
- [Linux](https://storage.googleapis.com/go-spacemesh-release-builds/v0.2.3-beta.0/Linux.zip)

2. Extract the zip file to a directory.

3. Navigate to the directory in terminal.

4. Configure downloaded binaries for execution.

#### Linux
```bash
chmod u+x go-spacemesh
chmod u+x smrepl_linux_amd64

```

#### macOS
```bash
chmod u+x go-spacemesh
chmod u+x smrepl_darwin_amd64
sudo xattr -rd com.apple.quarantine go-spacemesh
sudo xattr -rd com.apple.quarantine lib*
sudo xattr -rd com.apple.quarantine smrepl_darwin_amd64
```

5. Start a Spacemesh full node.

#### macOS and Linux
```bash
./go-spacemesh -c config.json > log.txt
```

#### Windows (PowerShell)

```PowerShell
.\go-spacemesh.exe -c config.json > log.txt
```

6. Start Smrepl.

#### macOS
```bash
./smrepl_darwin_amd64

```
#### Linux
```bash
./smrepl_linux_amd64
```

#### Windows (PowerShell)

```PowerShell
.\smrepl_windows_amd64.exe
```

Proceed to create a wallet and setup smeshing in smrepl.

----

### Using the gpu-post test app
Navigate to your directory you extract the zip release to and enter from a terminal:

#### macOS
```bash
export DYLD_LIBRARY_PATH=.:$DYLD_LIBRARY_PATH
sudo xattr -rd com.apple.quarantine gpu-setup-test
chmod +x gpu-setup-test
./gpu-setup-test
```

#### Linux
```bash
export LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH
chmod +x gpu-setup-test
./gpu-setup-test
```

#### Windows (PowerShell)
```PowerShell
.\gpu-setup-test.exe
```

The available commands should be displayed.

### Listing Supported POST compute devices (cpus and gpus)
```bash
./gpu-setup-test -l
```

### Benchmarking your gpu(s)
```bash
./gpu-setup-test -b
```

---

## Known Issues
- [Smeshing fails after node restart](https://github.com/spacemeshos/go-spacemesh/issues/2858). Mitigation: don't restart your node after starting to smesh. 

## Full Node Release on Github
- [go-spacemesh v0.2.3-beta.0](https://github.com/spacemeshos/go-spacemesh/releases/tag/v0.2.3-beta.0)