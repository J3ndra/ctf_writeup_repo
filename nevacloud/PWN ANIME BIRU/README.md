# HOW TO SOLVE Binary Exploitation (PWN) ANIME BIRU!

### EXAMINE THE CODE
In this challenge, we didn't need to explore the binary because we have the source code. We will see if our input must match the random int from `0` to `666666`, that's a rough stuff. But if you know, if python `input` function have vulnerability? [Read this article for more information](https://www.geeksforgeeks.org/vulnerability-input-function-python-2-x/)

### START THE EXECUTION
If you type the variable name, you will be granted to next step.

![step 1](images/Screenshot%20from%202023-11-10%2019-42-18.png)

But the plain text is return a reverse base64, how do we fix it? Well if you see the code again, they use `raw_input` for read our input. But `raw_input` also have vulnerability for RCE (Remote Code Execution). Yes, we can ran code in raw input. [read this article for more information](https://github.coventry.ac.uk/pages/CUEH/245CT/2_LinuxAndShells/RCE/)

Try to type `'; whoami; echo"A"'`, and you will see `kobo`. Which mean we actually gaining access to their server. Improve it with `'; cd /; ls; echo"A"'`. We will move to root directory with `cd /` and list the directory with `ls`. And you will see `flag.txt`.

![step2](images/Screenshot%20from%202023-11-10%2019-53-12.png)

Now run `'; cd /; cat flag.txt; echo"A"'` and you will rewarded with the flag.

![Result](images/Frame%202.png)