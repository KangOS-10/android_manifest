### KangOS ###

![KangOS](https://raw.githubusercontent.com/Travisholt92/KangOS/master/Images/KangOS.png)
<p align="center">

</p>

# Initialize Local Repository #
```bash
repo init -u https://github.com/KangOS-10/android_manifest.git -b 10
```

# Or Initialize Shallow Clone #
```bash
repo init --depth=1 -u https://github.com/KangOS-10/android_manifest.git -b 10
```

# Syncing Repository # 
```bash
repo sync -j$(nproc --all) --force-sync --no-tags --no-clone-bundle
```

# Building Environment #
```bash   
# Set up environment
. build/envsetup.sh

# Choose a target
lunch du_device-userdebug

# Build the ROM
make corvus
```
# XDA Template
[![XDA-Template](https://raw.githubusercontent.com/rashedsahaji/RandomStuff/master/XDADevelopers_button.png)](https://raw.githubusercontent.com/Corvus-ROM/android_manifest/10/xda)

# Telegram Support 
[![Telegram](https://raw.githubusercontent.com/rashedsahaji/RandomStuff/master/Telegram_button.png)](https://t.me/joinchat/GnTSyx3Aj0_L-9qT7dtG3w)

 Credits:
 =======

 * [**DirtyUnicorns**](https://github.com/DirtyUnicorns)
 * [**Corvus-ROM**](https://github.com/Corvus-ROM)
 * [**AOKP**](https://github.com/AOKP) The Original Masters of Kang

# Submitting Patches #

We would love to welcome new patches! Here is how..

Firstly register at https://review.corvusrom.com/

Open a terminal and generate the ssh keys
```bash
git config --global review.corvusrom.com.username <username you registered with>
git config --global review.corvusrom.com.email <your email you registered with>
ssh-keygen -t rsa -C "your@email.com"
```
After genrating the ssh key go to home/root "~/.ssh" and open "id_rsa.pub" and copy the whole key and paste it in our Gerrit settings (icon in the top right corner next to username) "SSH Keys" section on the left-hand side and then on "ADD NEW SSH KEY" and save it.

For submitting patches:-
```bash
cd PROJECT - Eg:- cd packages_apps_Settings
```
Do the changes you need to do and commit it
```bash
git add .
git commit -m "your sensible commit message that others will understand :P"
```
Ctrl X, then Y to save and Enter

To submit your changes:-
```bash
git push ssh://<username>@review.corvusrom.com:29418/<project> HEAD:refs/for/<branch>
```
Username :- i.e Your gerrit username (can be seen [**here**](https://review.corvusrom.com/settings))

Project :- i.e Your repository you are pushing to

Branch :- i.e The branch you are pushing to

Your final command will look like this:-
```bash
git push ssh://riteshm321@review.corvusrom.com:29418/android_packages_apps_Settings HEAD:refs/for/10
```
If you gonna make some extra additions, just repeat the steps (don't start a new patch), but instead of git commit -m use git commit --amend. Gerrit will recognize it as a new patchset. Also DO NOT change the Change-ID.

Incase if you need to add changeid hooks:-
```bash
cd <project>
scp -p -P 29418 <username>@review.corvusrom.com:hooks/commit-msg .git/hooks/
```
You can also install the hook globally in all local projects:-
```bash
cd <rom source>
repo forall -c 'gitdir=$(git rev-parse --git-dir); scp -p -P 29418 <username>@review.corvusrom.com:hooks/commit-msg ${gitdir}/hooks/'
```
For more detailed information visit [**here**](https://gerrit-review.googlesource.com/Documentation/intro-user.html)
