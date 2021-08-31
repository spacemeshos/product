# Spacemesh 0.2 Preview Release

Latest release: v0.2.0-rc7

> This early Spacemesh 0.2 preview release is intended for people who are comfortable with using the command line.

Follow these instructions to join the Spacemesh 0.2 devnet.

1. Download the Spacemesh release for your platform.

-[Windows](https://github.com/spacemeshos/go-spacemesh/releases/download/v0.2.0-rc7/windows.zip)
-[macOS](https://github.com/spacemeshos/go-spacemesh/releases/download/v0.2.0-rc7/macOS.zip)
-[Linux](https://github.com/spacemeshos/go-spacemesh/releases/download/v0.2.0-rc7/linux.zip)

2. Extract the zip file to a directory

3. Open a terminal session and navigate to the directory

4. Configure downloaded binaries

#### Linux and macOS

```bash
sudo u+x go-spacemesh
sudo u+x lib*
sudo u+x smrepl
```

#### macOS
Enable downloaded binaries execution:

```bash
sudo xattr -rd com.apple.quarantine go-spacemesh
sudo xattr -rd com.apple.quarantine lib*
sudo xattr -rd com.apple.quarantine smrepl
```

#### Windows 10
TBD

5. Start a Spacemesh full node:

#### macOS and Linux
```bash
./go-spacemesh -c config.json > log.txt`
```

#### Windows
TBD

6. Start smrepl

> Due to a known issue please wait for up to 45 seconds from the time you started your node in the previous to start smrepl.

#### macOS and Linux

```bash
./smrepl
```

Proceed to create a wallet and setup smeshing in smrepl.


----

## Technical Information

- [v0.2.0-rc7 on Github](https://github.com/spacemeshos/go-spacemesh/releases/tag/v0.2.0-rc7)

You can build this release from source code from our github repo.
