
| SL | Topics |
|--|--|
| 1 | [Sublime Text 4 setup](#sublime-text-4) |
| 2 | [Pre-compile C++ header file](#pre-compile-c-header-file-bitsstdch)|
| 3 | [Create custom snippets](#create-custom-snippets)|
| 4 | [Google style syntax](#configure-google-c-style)|

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

The following build system for sublime text will take input from **inputf.in** file and print output in **outputf.out**.The build file extension will be ``.sublime-build``.

    {
        "cmd": ["g++.exe", "-std=c++17", "${file}",
                "-o", "${file_base_name}.exe",
                "&&", "${file_base_name}.exe<inputf.in>outputf.out"],
        "shell":true,
        "working_dir":"$file_path",
        "selector":"source.cpp"
    }

### Console Input & Output
The following sublime build system will take input from **console** (cmd) and print output.

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


# Pre-compile C++ header file <bits/stdc++.h>
1. Open the directory: ``C:\MinGW\lib\gcc\mingw32\6.3.0\include\c++\mingw32\bits``
2. Then press **shift + right** click of the mouse and select **open powershell window here**.
3. Then paste the command ``g++ stdc++.h -std=c++17`` and hit enter


# Create custom snippets on Sublime Text 4
There is a website for generating snippets.
Link: [Snippet Generator](https://snippet-generator.app/)
You can use this website to generate snippets for Visual studio code, Sublime text and Atom.

## Sublime text C++ template snippet for competitive programming
Create a new snippet from Sublime Text 4: ``Tools > Developer > New Snippet``

Copy the following code and save it as **cp.sublime-snippet**.
File saving directory: ``C:\Users\${user}\AppData\Roaming\Sublime Text\Packages\User``

    <snippet>
      <content><![CDATA[
    #include <bits/stdc++.h>
    
    using namespace std;
    
    typedef long long ll;
    typedef vector<int> vi;
    typedef vector<long long> vl;
    
    #define TLE ios::sync_with_stdio(0); cin.tie(0); cout.tie(0);
    
    void Solution(int t) {
      // start coding from here
    }
    
    int main() {
      TLE;
      int test_case, t = 1;
      cin >> test_case;
      while (test_case--) {
        Solution(t++);
      }
    
      return 0;
    }
    ]]></content>
      <tabTrigger>cp</tabTrigger>
      <description>C++ template for competitive programming</description>
      <!-- Optional: Set a scope to limit where the snippet will trigger -->
      <!-- <scope >source.python</scope > -->
    </snippet>

## Sublime text basic C++ template snippet
Copy the following code and save it as **cpp.sublime-snippet**.
File saving directory: ``C:\Users\${user}\AppData\Roaming\Sublime Text\Packages\User``

    <snippet>
      <content><![CDATA[
    #include <iostream>
    
    using namespace std;
    
    int main() {
    
    	return 0;
    }
    ]]></content>
      <tabTrigger>cpp</tabTrigger>
      <description>Basic C++ template</description>
      <!-- Optional: Set a scope to limit where the snippet will trigger -->
      <!-- <scope >source.python</scope > -->
    </snippet>


# Configure Google C++ Style 
1. Install ``SublimeAStyleFormatter`` plugin
2. Goto ``Preferences > Package Settings > SublimeAStyleFormatter > Settings - User`` and add the following configuration

    {
        "autoformat_on_save": true,
        "options_default": {
            "style": "google",
        }
    }
Now whenever you will press ``crtl + s``, your file will be saved using google style syntax.
