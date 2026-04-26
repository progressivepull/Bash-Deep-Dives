# Bash Commands

# 🧩 How Git Bash finds commands

Git Bash searches for commands in the directories listed in the PATH environment variable. If your script’s folder is in PATH, you can run it from anywhere just by typing its name.

Common Git Bash PATH directories include:

* /usr/bin
* /usr/local/bin
* ~/bin (you can create this yourself)

Git for Windows provides a Bash emulation that behaves like Linux/Unix, so these conventions work the same way.

## Add your own folder to PATH (recommended)
Create a folder for your scripts:

```
mkdir -p ~/bin
```
Move your script into it:

```
mv myscript.sh ~/bin/
```
Make it executable:

```
chmod +x ~/bin/myscript.sh
```

Add this line to your ~/.bashrc:

```
export PATH="$HOME/bin:$PATH"
```
Reload Git Bash:

```
source ~/.bashrc
```
Now you can run it anywhere:

```
myscript.sh
```
----


# [README](./../README.md)
