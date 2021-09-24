# simplec
A bash script to write, compile, and/or debug C or C++ code.
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
