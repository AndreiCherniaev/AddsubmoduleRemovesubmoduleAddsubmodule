# 0) Clone my example repo
Simple way
```
git clone --remote-submodules --recurse-submodules -j8 https://github.com/AndreiCherniaev/AddsubmoduleRemovesubmoduleAddsubmodule.git
cd AddsubmoduleRemovesubmoduleAddsubmodule/
```
Or in several steps
```
git clone https://github.com/AndreiCherniaev/AddsubmoduleRemovesubmoduleAddsubmodule.git
cd AddsubmoduleRemovesubmoduleAddsubmodule/
git submodule update --remote --merge
```

# 1) Add Buildroot as submodule
This step is already done in current repo. So you shouldn't do it.
```
$ git submodule add -b master https://github.com/buildroot/buildroot myBuildroot/buildroot
$ git commit -m "add submodule"
$ git push
```

# 2) Remove submodule Buildroot
```
$ git rm -f myBuildroot/buildroot
```
# 3) Add Buildroot as submodule again
```
$ git submodule add -b master https://github.com/buildroot/buildroot myBuildroot/buildroot
fatal: A git directory for 'myBuildroot/buildroot' is found locally with remote(s):
  origin	https://github.com/buildroot/buildroot
If you want to reuse this local git directory instead of cloning again from
  https://github.com/buildroot/buildroot
use the '--force' option. If the local git directory is not the correct repo
or you are unsure what this means choose another name with the '--name' option.
```
Because I already have folder 'myBuildroot/buildroot' in my computer, you can remove the folder
```
rm -rf .git/modules/myBuildroot/buildroot
git config --remove-section submodule.myBuildroot/buildroot
```
And go to step 1). Another way to do step 3) is to remove the repo from your computer and clone again from Github, then you can do step 1). Tested with git version 2.34.1
