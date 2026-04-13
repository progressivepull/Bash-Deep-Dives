# Bash-Deep-Dives

## **Open WSL Ubuntu Command Line**

Click the Ubuntu icon in the Start Menu to launch your WSL Ubuntu terminal.     

![ubuntu.png](https://github.com/progressivepull/Bash-Deep-Dives/blob/main/resource/ubuntu.png)

## **From Ubuntu Command Line**

### Activating your Python virtual environment
**source ~/jupyterenv/bin/activate** activates a Python virtual environment located in your home 
directory under jupyterenv. The command tells your shell to load the environment’s settings so 
that Python, pip, and installed packages come from that environment instead of the system default.

``` bash
source ~/jupyterenv/bin/activate
```

### Moving into your Windows folder
That command shows two things happening at once: you are inside your virtual environment **(jupyterenv)** 
and you are changing directories into your Windows Documents folder as mounted inside WSL.

``` bash
cd /mnt/c/Users/<USER_NAME>/Documents
```
**For Example:**      

``` bash
cd /mnt/d/pinkt/Documents/GitHub-ProgressivePull/Bash-Deep-Dives
```
### Launching Jupyter Notebook

To start Jupyter Notebook with the working directory set to ```C:/User/<Users>/Documents```, launch it 
from a shell that is already in that folder. That ensures Jupyter uses that location as its file root.

``` bash
jupyter notebook

```
## Explaination
Here’s what those three lines are doing — they’re basically the
*perfect* workflow for running Jupyter Notebook from WSL while keeping
your files on Windows.

**🧠 The short version**

You are:

1.  **Activating your Python virtual environment** (so Jupyter + the
    Bash kernel are available)

2.  **Moving into your Windows folder** (so notebooks save
    where you want them)

3.  **Launching Jupyter Notebook** (running inside WSL, opening in
    Windows)

That’s the whole story — but let me break down each line so it’s crystal
clear.

**💡 Line‑by‑line explanation**

**1️⃣ source ~/jupyterenv/bin/activate**

This activates the virtual environment you created earlier.

- It switches your shell into an isolated Python environment

- That environment contains your installed packages: notebook,
  bash_kernel, etc.

- Your prompt changes to:

```
(jupyterenv) pinkt@JOHN:~\$
```

which tells you the venv is active.

Without this step, jupyter notebook wouldn’t run because the system
Python is locked down by Ubuntu’s PEP 668 rules.

**2️⃣ cd /mnt/c/Users/pinkt/Documents**

This moves you into your **Windows Documents folder**, but from inside
WSL.

- /mnt/c/... is how WSL mounts your Windows C: drive

- Anything you save here is stored on Windows, not inside Linux

- This is ideal because:

  - Files are easy to find in File Explorer

  - VS Code can open them directly

  - Backups/sync (OneDrive, etc.) work normally

Your prompt updates to:

```

(jupyterenv) pinkt@JOHN:/mnt/c/Users/pinkt/Documents\$

```

This means: **“I’m in Windows storage, but using Linux tools.”**

**3️⃣ jupyter notebook**

This launches the Jupyter Notebook server **inside WSL**, using the
Python environment you activated.

What happens next:

- The server runs in Linux

- Your browser opens in Windows

- The notebook files save to your Windows Documents folder

- Kernels (Python, Bash, etc.) execute inside WSL

This is the best of both worlds: **Windows UI + Linux compute + clean
file storage.**

**🧩 Why this workflow is correct**

You’re doing exactly what WSL is designed for:

- Keep your environment isolated and clean

- Avoid system Python restrictions

- Store notebooks where Windows apps can see them

- Run kernels in Linux for compatibility and performance

This is the same setup used by data scientists who work across Windows +
WSL.

# **🧰 Core Bash Commands with Examples**

- **cd** — change directory
 
``` bash
$ cd /mnt/c/Users/<USER>/Documents
```

- **ls** — list files 

``` bash
$ ls -lah
```

- **pwd** — show current directory 

``` bash
$ pwd
```

- **mkdir** — create a folder 

``` bash
$ mkdir project_folder
```

- **rm** — remove files or folders 

``` bash
$ rm file.txt 
$ rm -r old_directory
```

- **cp** — copy files or folders 

``` bash
$ cp notes.txt backup_notes.txt
$ cp -r src/ src_backup/
``` 

- **mv** — move or rename 

``` bash
$ mv oldname.txt newname.txt  
$ mv file.txt /mnt/c/Users/<USER>/Documents
```


- **touch** — create an empty file 

``` bash
$ touch script.sh
```

- **cat** — print file contents 

``` bash
$ cat config.yaml
```

- **nano** — edit a file in terminal 

``` bash
$ nano script.sh
```

- **grep** — search text 

``` bash
$ grep "error" logfile.txt
```

- **find** — locate files 

``` bash
$ find . -name "\*.py"

```

- **chmod** — change permissions 

``` bash
$ chmod +x script.sh
```

- **echo** — print text or write to file 

``` bash
$ echo "Hello" > hello.txt

```

- **which** — show command location 

``` bash
$ which python
```

- **ps** — list running processes 


``` bash
$ ps aux
```

- **kill** — stop a process kill 1234

``` bash
$ kill 1234
```

- **history** — show previous commands 

``` bash
$ history \| grep cd
```

- **man** — open manual pages 

``` bash
$ man ls
```

## 🧩 Useful combinations
* List files sorted by size:

``` bash
$ ls -lhS
```

* Search inside all .log files:

``` bash
$ grep -R "timeout" *.log
```

* Copy everything except certain files:

``` bash
cp -r !(node_modules) backup/ (requires extglob)
```

* Run a script:

``` bash
./script.sh
```