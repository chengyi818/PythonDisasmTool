# PythonDisasmTool
A toolkit to show python byte code

# 说明
人生苦短,我用Python.
在学习Python源码的过程,不可避免的需要对照Python字节码来学习.本小工具用于查看python文件所对应的字节码.
支持查看Python源码对应的各版本字节码.

## 示例
`test.py`是我们想查看的文件.
```
def main():
    print("hello world!")

if __name__ == "__main__":
    main()
```

## 查看python3所对应的字节码
### 输入
```
python3 pydis.py test.py
```
### 输出
```
main
  2           0 LOAD_GLOBAL              0 (print)
              3 LOAD_CONST               1 ('hello world!')
              6 CALL_FUNCTION            1 (1 positional, 0 keyword pair)
              9 POP_TOP
             10 LOAD_CONST               0 (None)
             13 RETURN_VALUE
---------------------------
<module>
  1           0 LOAD_CONST               0 (<code object main at 0x7f003b4ded20, file "test.py", line 1>)
              3 LOAD_CONST               1 ('main')
              6 MAKE_FUNCTION            0
              9 STORE_NAME               0 (main)

  4          12 LOAD_NAME                1 (__name__)
             15 LOAD_CONST               2 ('__main__')
             18 COMPARE_OP               2 (==)
             21 POP_JUMP_IF_FALSE       31

  5          24 LOAD_NAME                0 (main)
             27 CALL_FUNCTION            0 (0 positional, 0 keyword pair)
             30 POP_TOP
        >>   31 LOAD_CONST               3 (None)
             34 RETURN_VALUE
---------------------------
```

## 查看python2所对应的字节码
### 输入
```
python2 pydis.py test.py
```
### 输出
```
main
  2           0 LOAD_CONST               1 ('hello world!')
              3 PRINT_ITEM
              4 PRINT_NEWLINE
              5 LOAD_CONST               0 (None)
              8 RETURN_VALUE
---------------------------
<module>
  1           0 LOAD_CONST               0 (<code object main at 0x7f59874a21b0, file "test.py", line 1>)
              3 MAKE_FUNCTION            0
              6 STORE_NAME               0 (main)

  4           9 LOAD_NAME                1 (__name__)
             12 LOAD_CONST               1 ('__main__')
             15 COMPARE_OP               2 (==)
             18 POP_JUMP_IF_FALSE       31

  5          21 LOAD_NAME                0 (main)
             24 CALL_FUNCTION            0
             27 POP_TOP
             28 JUMP_FORWARD             0 (to 31)
        >>   31 LOAD_CONST               2 (None)
             34 RETURN_VALUE
---------------------------
```
