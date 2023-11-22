# 0) Clone my example repo
Simple way
```
git clone --remote-submodules --recurse-submodules -j8 https://github.com/AndreiCherniaev/AddsubmoduleRemovesubmoduleAddsubmodule.git
cd AddsubmoduleRemovesubmoduleAddsubmodule/
```
Or several-steps way
```
git clone  https://github.com/AndreiCherniaev/AddsubmoduleRemovesubmoduleAddsubmodule.git
cd AddsubmoduleRemovesubmoduleAddsubmodule/
git submodule update --remote --merge
```

# 1) Add Buildroot as submodule
```
$ git submodule add -b master https://github.com/buildroot/buildroot myBuildroot/buildroot
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
Becase I already have folder 'myBuildroot/buildroot' in my computer. You can remove folder
```
rm -rf .git/modules/myBuildroot/buildroot
git config --remove-section submodule.myBuildroot/buildroot
```
And go to step 1). Another way to do step 3) is remove repo from your computer and clone again fror github, then you can do step 1). Tested with git version 2.34.1
