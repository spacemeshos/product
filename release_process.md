## Releasing a new go-spacemesh Relase
1. Prepare a node releasesa and tag it e.g. v0.1.12. This determines which features and fixes are in this releases.
1. Build go-spacemesh node binaries from the tag for all 3 platforms.
1. Create a new github release from the tag and add links to download the 3 node binaries built in step 2
1. Write summarizerd releases notes in the github release.

## Releasing a new Spacemesh app release
1. Determine which go-sacemesh binaries versions shjould be built with the app. e.g. v0.1.12 and the app release version. e.g. v0.0.12.
1. Create a tag for the realease code in github. e.g. v0.0.12. This determines which app code should be built for this release.
1. Build app installers for all 3 platforms from the tagged code and with the specified full node release for each platform.
1. Create a new github release for the release github tag and publish link to 3 built installers in that release.
1. Write Release Notes in the github release.
1. Link to full node release from the github release.
1. Update installer links in Spacemesh website and testnet guide.
