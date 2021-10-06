# Spacemesh 0.2 Preview Release

Latest release: v0.2.3-beta.0 (Network Id 207)

> This early Spacemesh 0.2 technical preview release is intended for users who are comfortable using the command line and terminal applications.

Follow these instructions to join the Spacemesh 0.2 devnet.

## System Requirements

- A computer with a modern Intel, an AMD CPU (2 cores / 4 native threads) or an Apple M1 CPU.
- Windows 10 Home or Pro, macOS, Ubuntu 18.04, Fedora 21, or Debian 8.
- 4 GB RAM.
- 250 GiB free disk space (HDD or SSD).
- An always-on, un-metered Internet connection capable of 10 mbps download and 1 mbps upload.
- Recommended but not required: A graphics card supporting CUDA compute API 9.0 or later, or Vulkan compute API 1.1 or later.

## Installing & Running

1. Download the devenet release zip file for your platform

- [Windows](https://storage.googleapis.com/go-spacemesh-release-builds/v0.2.3-beta.0/Windows.zip)
- [macOS](https://storage.googleapis.com/go-spacemesh-release-builds/v0.2.3-beta.0/macOS.zip)
- [Linux](https://storage.googleapis.com/go-spacemesh-release-builds/v0.2.3-beta.0/Linux.zip)

2. Extract the zip file to a directory

3. Navigate to the directory in terminal

4. Configure downloaded binaries

#### Linux and macOS
Set binaries execution permissions.

```bash
chmod u+x go-spacemesh
chmod u+x smrepl
```

#### macOS
Enable downloaded binaries execution.

```bash
sudo xattr -rd com.apple.quarantine go-spacemesh
sudo xattr -rd com.apple.quarantine lib*
sudo xattr -rd com.apple.quarantine smrepl
```

5. Start a Spacemesh full node

#### macOS and Linux
```bash
./go-spacemesh -c config.json > log.txt
```

#### Windows (PowerShell)

```PowerShell
.\go-spacemesh.exe -c config.json > log.txt
```

6. Start Smrepl

#### macOS and Linux

```bash
./smrepl
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

---

## Known Issues
- [Smeshing fails after node restart](https://github.com/spacemeshos/go-spacemesh/issues/2858). Mitigation: setup smeshing and don't restart your node. 