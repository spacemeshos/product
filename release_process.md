Creating a new go-spacemesh release
1. Prepare a node releasesa and tag it e.g. v0.1.12. This determines which features and fixes are in this releases..
1. Build go-spacemesh nodes from the tag for all 3 platforms.
1. Create a new github release from the tag and add links to download the 3 node binaries built in step 2.
1. Write summarizerd releases notes in the github release.

Creating a new Spacemesh app release
1. Create a tag for the realease code in github. e.g. v0.0.12. This determines which code should be built.
1. Determine which go-sacemesh binaries versions shjould be built with the app. e.g. v0.1.12.
1. Build app installers for all 3 platforms from the tagged code with the specified node releases.
1. Create a new github release for the tag and publish link to 3 built installers in that release.
1. Write release Release Notes.
1. Update installer links in Spacemesh website and testnet guide.
