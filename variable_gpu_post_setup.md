# Basic Interaction via GUI

1. User selects desired post commitment size. e.g. 100GB, 200GB, etc...
2. User selects path where the post commitment file(s) should be created.
3. App selects a processor to use for POST setup from a list processors available on his system.

Technical notes:
  - This list always includes the main system CPU as a fall-back processor.
  - The list includes each GPU available to the system which is supported by post-gpu. A system may have 0 or more supported GPUs.
  - User should be made aware that using the CPU can be x5-15 times slower then using his GPU.
  - The spacemesh post-gpu c library should be used to enumerate system processors.
  - We need this step to give user full control of the post generation process.

4. The post commitment job is started. Note that is should fallback at times of interactivity and continue at full speed when a user is not interactively using the system.
