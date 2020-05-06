# Basic Interactions

## Setup POST commitment
1. User selects desired post commitment size. e.g. 100GB, 200GB, etc...
2. User selects path where the post commitment file(s) should be created. This needs to be on a volume that as at least as much free space as the commitment size. The app should verify that this is the case before allowing the user to proceed to step #3.
3. App selects a processor to use for post setup from a list processors available on his system.

    Technical notes:
    - This list always includes the main system CPU as a fall-back processor. It should always be the last item.
    - The list includes each GPU available to the system which is supported by post-gpu. A system may have 0 or more supported GPUs.
    - User should be made aware that using the CPU can be x5-15 times slower then using his GPU.
    - The spacemesh post-gpu c library should be used to enumerate supported system processors. It implements this capability.
    - We need this step to give user full control of the post generation process.
    - Most systems will have 1 supported GPU and 1 CPU. In this case. Select the supported GPU by default as this is what we recommend to use so it is a good default.

4. User is notified that the process has started and that he can check progress in the same screen. e.g. Smesher screen. The app should also send a desktop notification when post setup init is complete.
    - The post commitment job should be started. Note that is should fallback at times of interactivity and continue at full speed when a user is not interactively using the system.
