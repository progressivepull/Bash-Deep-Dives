# Bash-Deep-Dives

## **Open WSL Ubuntu Command Line**

Click on Ubuntu Icon from the Start Menu.      

![ubuntu.png](https://github.com/progressivepull/Bash-Deep-Dives/blob/main/resource/ubuntu.png)

## **From Ubuntu Command Line**

``` bash

pinkt@JOHN:~\$ source ~/jupyterenv/bin/activate

(jupyterenv) pinkt@JOHN:~\$ cd /mnt/c/Users/pinkt/Documents (jupyterenv)

pinkt@JOHN:/mnt/c/Users/pinkt/Documents\$ jupyter notebook

```

Here’s what those three lines are doing — they’re basically the
*perfect* workflow for running Jupyter Notebook from WSL while keeping
your files on Windows.

**🧠 The short version**

You are:

1.  **Activating your Python virtual environment** (so Jupyter + the
    Bash kernel are available)

2.  **Moving into your Windows Documents folder** (so notebooks save
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
