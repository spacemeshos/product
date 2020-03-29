# New User Experience Testing Setup
1. Quit the smapp if it is running.
2. Delete local Spacemesh data folder. Folder location:
  - OS X: `your_hd/users/[your_user_name]/Application Support/Spacemesh`
  - Windows 10: `c:\Users\[your_user_name]\AppData\Roaming\Spacemesh`
  - Linux: `~/.config/Spacemesh`
3. Verify there's no process called go-spacemesh running on the system. If there is kill it.
4. In Windows 10, if the app was installed then uninstall it by running `Uninstall Spacemesh.exe`. It is located in the App install folder. The default is: `C:\Users\[your_user_name]\AppData\Local\Programs\Spacemesh`
5. Install the app for testing and run it.

# App Update Experience Testing Setup
1. Quit the smapp if it is running.
2. Verify there's no process called go-spacemesh running on the system. If there is kill it.
3. In Windows 10, if the app was installed then uninstall it by running `Uninstall Spacemesh.exe`. It is located in the App install folder. The default is: `C:\Users\[your_user_name]\AppData\Local\Programs\Spacemesh`
4. Install the updated app for testing and run it.

# Sanity Test
1. Setup smeshing and wallet
2. Wait until app is synced with the mesh.
3. Get some smidge from the tap and verify that transaction is confirmed and wallet balance updated.
4. Send some smidge to another account and verify that the transaction gets pending and confirmed.
5. Verify smeshers is starting to get rewards in up to 49 hours from setup time.
6. Check the smeshing rewards and transactions are visible in the smesher log, in the main wallet screen and in the full transaction log.
