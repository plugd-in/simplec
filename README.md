# simplec
A bash script to write, compile, and/or debug C or C++ code.

## Installation
Technically, you can run this through curl, straight into bash. I don't recommend piping scripts into bash.

### Step 1
First, check whether ~/bin is in your path:  
`echo $PATH | grep "/home/.*/bin" | diff <(cat /dev/stdin) <( echo $PATH ) -sq`  
The command output should look like: `Files /dev/fd/63 and /dev/fd/62 are identical` or `Files /dev/fd/63 and /dev/fd/62 differ`

If your output says that your "files" differ, then ~/bin is not in your path (go to step 2).  
Otherwise, in the case where your "files" are identical, skip to step 3.

### Step 2
Create a directory where you can place the script, or ensure that it's already created.  

Run the following:  
`mkdir -p ~/bin`  

Afterwards, you need to make sure that executable files are in your $PATH. This means adding ~/bin to the $PATH:  
`echo "PATH=\"$PATH:~/bin\"" >> ~/.bashrc`  

Reload your terminal session so that the changes can take place.  
### Step 3
Navigate to your ~/bin directory.  
`cd ~/bin`

Download the script:
`curl -o simplec 'https://raw.githubusercontent.com/plugd-in/simplec/main/simplec'`  

Peruse the contents of the script, so that you know what you are letting run on your system.  

### Step 4
You'll want to make sure that you can execute the script, as the file shouldn't be executable yet.  

In order to make the file executable, run the following:  
`chmod +x simplec`

You should now be able to run the command `simplec`  

### Step 5 (optional)
Ensure that you have a text editor. By default, the script uses the EDITOR set in your $EDITOR variable.  

Run `$EDITOR` to try out the editor you have set (may be nano by default). If you're fine with it, then good for you, you're done.  

If you want to change your editor, for example set it to Vim (which I recommend), run the following:  
`sudo apt install vim ; echo "EDITOR=$(which vim)" >> ~/.bashrc`

Note, that the editor mustn't fork, so that when you exit the next part of the script (compilation) runs.

## Syntax
simplec \[flags\]  
  -p  Input script to edit, compile, and run/debug. Optional.  
  -o  Output location for the compiled binary. Optional.  
  -g  Use GDB to debug the code.  
  -a  Arguments to pass to binary. Ex: "simplec -a 'foo bar'"  
  -l  Use CPP libraries while compiling.  
  -c  Clear/remove the input file.  
  -d  Clear/remove the compiled binary.  
## Defaults
The input file defaults to /tmp/$UUID.$LANG, where LANG can be c or cpp.
The output file defaults to /tmp/$UUID. In the case where either is set to the default, they are cleared upon exit.

If an input is specified, but a language is not, then the language is inferred by the file extension.
