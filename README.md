# FreeIPAClientAddUserSudo
This small script is needed as an addition to configuring FreeIPA on Linux Mint, namely... Takes users from the `ipa_sudo` group (can be reconfigured) and adds them to the local sudo user group. </br>
This is necessary so that administrators from the `IPA` domain are visible in the graphical environment, because often shells such as `KDE`, `Cinnamon` and the like display users only from the `/etc/group` group. </br>
I don't know who will find this useful... But if you need to prepare a clean system for the IPA domain - go ahead :) </br>
There are 4 variables in the script, you will most likely only need `nameIPAGroup`. </br>
Insert here the name of the group of users in the IPA domain that should be sudo and local to the system. </br>

# About script
If you want to know more about the script, it works as follows: </br>
- First, the system is updated and the necessary packages are installed (Tree is not required).
- Then a sh file is created that will be executed by the future `service` and is located along the path: `/usr/local/bin/ipa-client-add-user-sudo.sh` The path is also described in a variable: `fileNameBash`
- Next, the `service` file itself is created, which will only be executed when the system starts or when manually called. The file is located at the path: `/etc/systemd/system/ipa-client-add-user-sudo.service` The path is also described in a variable: `fileNameService`
- Then the `service` is `unmasked`, `enabled` and `started`, and after the service is executed or crashed, its `status` is displayed.
