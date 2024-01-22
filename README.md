# The CS 3110 ARM-Processor VM

Instructions for creating VM on M* processors Macs.

You can download the CS 3110 VM from [Cornell Box][3110vm]. Installation and
usage instructions can be found in the [3110 textbook][op-vm]. Here is how we
created the VM:

[3110vm]: https://cornell.box.com/v/cs3110vm-2024sp
[op-vm]: https://cs3110.github.io/textbook/chapters/appendix/vm.html
1/18/2024
[VMWare Fusion Player]: https://customerconnect.vmware.com/en/evalcenter?p=fusion-player-personal-13
[Ubuntu 22.04.3 jammy-desktop-arm64.iso]: https://cdimage.ubuntu.com/jammy/daily-live/current/

1. Download and install [VMWare Fusion Player], and download [Ubuntu 22.04.3 jammy-desktop-arm64.iso]

   - Create a new VM in VMWare Fusion Player. Name it `cs3110vm-2024sp-ubuntu`, replacing
     `2024sp` with the current semester. Skip the unattended install. Use 2048
     MB RAM, 1 CPU, and a 64 GB dynamically-sized hard drive. We deliberately
     keep the hardware requirements minimal for students who have lower-end
     hardware. But the drive needs to have room to grow for projects later in
     the semester.

   - Install Ubuntu. Choose the minimal install (i.e., fewer apps). Choose to
     download updates during the install. Make your name "OCaml Programmer",
     the computer name "cs3110vm", and the username and password both "camel",
     and choose "log in automatically".

   - After installation and rebooting, you'll be asked to enable a bunch of
     features such as online accounts, Ubuntu Pro, and developer error
     reporting. Don't enable them, since students should make those choices
     themselves.

   - Soon after rebooting, Software Updater will want to install updates. Let
     it. Then reboot again.

2. Open Terminal. Right-click and add it to favorites. Run
   ```
   sudo apt update
   sudo apt upgrade
   sudo apt install build-essential linux-headers-$(uname -r) vim emacs open-vm-tools
   ```


3. To install and initialize OPAM, run
   ```
   sudo apt install pkg-config opam
   opam init --bare -a -y
   ```
   Then follow the install instructions in the [CS 3110 textbook][op] to create
   an OPAM switch and install required packages for the current semester. Logout (or
   reboot) to get the `.profile` changes working in all new shells.

4. Use the Ubuntu Software installer to install Visual Studio Code. (Update any other software it wants to at the same time.) Then launch
   VSC and add it to favorites. Copy-paste `vsc_settings.json` into user
   settings. Install the "OCaml Platform" extension. Create a `~/3110` folder
   and test that OCaml language support is working. Make sure not to leave any
   files or folders open when you close it, otherwise they will be opened in the
   distributed VM.

5. Download the (free) caravan wallpaper.
   ```
   cd ~/Pictures
   wget https://wonderfulengineering.com/wp-content/uploads/2016/01/eqypt-wallpaper-12.jpg
   ```
   Set it as the desktop background. It is also cached locally here in this repo
   at `caravan.jpg`.

6. Run `sudo usermod -a -G vboxsf camel` to give the account access to shared
   folders. Create a shared folder to test they are working, then delete it and
   any others that might exist. The instructions to create shared folders are in
   the textbook appendix. Note that shutting down the VM really does seem to be
   necessary when modifying these settings.

7. Delete `.utop-history` and finally delete `.bash_history`.

8. If you've resized the window, resize it back so that it's fairly small,
   otherwise when students bring it up on their own small monitor it might not
   fit. The size of the VirtualBox boot window is good.

9. Shutdown the machine. Double check the VM settings in VirtualBox to solve any
   invalid configuration issues. Make sure the display scale factor is 100%,
   especially if you have a Retina display.

10. Export the appliance.

[VirtualBox]: https://www.virtualbox.org/wiki/Downloads
[ubuntu]: https://releases.ubuntu.com/22.04/
[op]: https://cs3110.github.io/textbook/
