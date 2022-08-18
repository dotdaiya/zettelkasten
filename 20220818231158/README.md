# Make cmder navigation easy

To make navigation easier:

```bat
# Create dir for storing symbolik links
mkdir ~/symlinks
# Create a symbolic link in cmd
mklink /j  <directory/shortcut name> <directory to create the link to>
```

```bash
# quick access to symlinks
export CDPATH=~/symlinks
```

If you want these to persist each *bash* session just include it in `config/user_profile.sh`.
