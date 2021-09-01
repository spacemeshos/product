# Spacemesh 0.2 Preview Release

Latest release: v0.2.0-rc7 (Network Id 203)

> This early Spacemesh 0.2 technical preview release is intended for users who are comfortable with using the command line and terminal applications.

Follow these instructions to join the Spacemesh 0.2 devnet.

1. Download the Spacemesh release for your platform

- [Windows](https://github.com/spacemeshos/go-spacemesh/releases/download/v0.2.0-rc7/windows.zip)
- [macOS](https://github.com/spacemeshos/go-spacemesh/releases/download/v0.2.0-rc7/macOS.zip)
- [Linux](https://github.com/spacemeshos/go-spacemesh/releases/download/v0.2.0-rc7/linux.zip)

2. Extract the zip file to a directory

3. Navigate to the directory in terminal

4. Configure downloaded binaries

#### Linux and macOS
Set binaries execution permissions.

```bash
chmod u+x go-spacemesh
chmod u+x lib*
chmod u+x smrepl
```

#### macOS
Enable downloaded binaries execution.

```bash
sudo xattr -rd com.apple.quarantine go-spacemesh
sudo xattr -rd com.apple.quarantine lib*
sudo xattr -rd com.apple.quarantine smrepl
```

Or alternatively try

```bash
spctl --add go-spacemesh
spctl --add lib*
spctl --add smrepl
```


5. Start a Spacemesh full node

#### macOS and Linux
```bash
./go-spacemesh -c config.json > log.txt
```

#### Windows (PowerShell)

```
.\go-spacemesh.exe -c config.json > log.txt
```

6. Start smrepl

> Due to a known issue please wait for up to 45 seconds from the time you start the go-spacemesh node in the previous step before starting smrepl.

#### macOS and Linux

```bash
./smrepl
```

#### Windows (PowerShell)

```
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
./gpu-setup-test -l
```

#### Linux
```bash
export LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH
chmod +x gpu-setup-test
./gpu-setup-test -l
```

#### Windows (PowerShell)
```
.\gpu-setup-test.exe -l
```

---

## Building from Source Code

> You can join the devnet by building this release binaries from source code from our public github repos instead of using our provided binaries.

1. Clone and build go-spacemesh [from this tag](https://github.com/spacemeshos/go-spacemesh/tree/v0.2.0-rc7)

2. Clone and build smrepl [from this tag](https://github.com/spacemeshos/smrepl/tree/v0.1.32)

3. Clone and build gpu-post [from this tag](https://github.com/spacemeshos/gpu-post/tree/v0.1.22)

4. Copy the gpu-post artifacts for your platform to your go-spacemesh directory.

5. Run the full node with this devnet [config file](https://github.com/spacemeshos/go-spacemesh/releases/download/v0.2.0-rc7/config.json)