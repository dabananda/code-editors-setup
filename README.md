# Sublime Text 4

Download and install **Sublime Text 4** from the following link.
Download: [Sublime Text 4](https://www.sublimetext.com/)

I have used **Fira Code** as my font in sublime text.
Download: [Fira Code](https://github.com/tonsky/FiraCode)

## Preferences setup
1. Open Sublime Text and press ``crtl+shift+p``
2. Then search for ``Install Package Control`` and install it
3. ``Preferences > Package Control > Install package``
4. Search for ``ayu`` and install it
5. Now open the link and copy the preferences [Preferences.sublime-settings](https://github.com/dabananda/code-editors-setup/blob/main/sublime_text/Preferences.sublime-settings)
6. Goto ``Preferences > Settings`` and paste the copied preferences and save it

That's all for preferences


## Create a new C++ build system

### File Input & Output

The following build system for sublime text will take input from **input.txt** file and show output in **output.txt**

    {
      "cmd": ["g++.exe", "-std=c++17", "${file}",
              "-o", "${file_base_name}.exe",
              "&&", "${file_base_name}.exe<input.txt>output.txt"],
      "shell":true,
      "working_dir":"$file_path",
      "selector":"source.cpp"
    }

### Console Input & Output
The following sublime build system will take input from **console** (cmd) and show output.

    {
      "cmd": ["g++.exe", "-std=c++17", "-o", "$file_base_name", "$file", "&&", "start", "cmd", "/c", "$file_base_name & echo. & echo. & pause"],
      "shell": true,
      "selector": "source.c++"
    }


Save the build file to ``C:\Users\${user}\AppData\Roaming\Sublime Text\Packages\User``

## Open Sublime Text 4 from command line (Windows)

1. Open the **Start Menu** and type ``environment``
2. Select the item **Edit the system environment variables**
3. Click the button **Environment Variables** at the bottom of the System Properties dialog
4. Select, or create, the **Path** environment variable in the appropriate section:
	- For the **current user**, select Path in the **User variables for {username}** section
	- For **all users**, select Path in the **System variables section**
6. Click the **New** button and add an entry with the Sublime Text installation directory
	- 64bit installs are typically in ``C:\Program Files\Sublime Text\``
	- 32bit installs on a 64bit version of Windows will be in ``C:\Program Files (x86)\Sublime Text\``
	- 32bit installs on a 32bit version of Windows will be in ``C:\Program Files\Sublime Text\``
