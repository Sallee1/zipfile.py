# zipfile.py
Zipfile module with encoding parameter

# How to Use
## As a EXTRA module (recommended)##
After renaming the file (myzipfile.py) with the program, you can use the `import ... as ...` to rename to adopt the old code (`import myzipfile as zipfile`)
## Replace the original zipfile module (not recommended, program may not be portable)
In the **Lib** folder under the python path

---
*Since this file is not a standard library, encoding may not have code hints. Please enter this parameter `encoding` manually.*

# Description
The file list of python's default zipfile module only supports cp437 and UTF8 encoding, whereas zip in Windows of Chinese often uses GBK to store the file list, which causes zip decompression using Python to scramble, requires reading ZipInfo to decompress the file one by one and renaming it, and illegal characters (?\*: "\ / |) may appear in the scrambled code causing the file decompression to fail.

Here I add the optional parameter `encoding` to ZipFile's constructor, which is the same as FileIO, and replace the file name decoding part with the `encoding`. The default parameter is utf8. After specifying the code page, ZipInfo saves the file name as the correctly decoded file name. The `extractall()` method also works correctly.

# 用法
## 作为第三方模块（推荐）
将该文件改名后（myzipfile.py）和程序放在一起，导入时可以使用`import ... as ...`改名来兼容旧代码（`import myzipfile as zipfile`）

## 替换原版zipfile模块（不推荐，程序可能会无法移植）
放在python路径下的Lib文件夹里

---
*由于该文件并不是标准库，`encoding`可能不会有代码提示，请手动输入此参数。*

# 说明
python默认的zipfile模块的文件列表只支持cp437和UTF8两种编码，而中文操作系统中zip常使用gbk来存储文件列表，这使得使用python解压zip会乱码，需要读取ZipInfo逐个解压文件并且重命名，并且乱码中可能会出现非法字符（?\*:"\/|）导致文件解压失败。
这里我在ZipFile的构造函数中添加了可选参数`encoding`，用法和文件IO相同，并且将文件名解码部分替换成了`encoding`指定的编码，默认参数为“utf8”，指定代码页之后，ZipInfo保存的文件名均为正确解码后的文件名。`extractall()`方法也可以正常的工作。
