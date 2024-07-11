# fileinput
`import fileinput` 是一个Python标准库中的模块，它提供了一种方便的方式来逐行处理多个输入流（文件或者标准输入）。主要用途是在读取文件时可以处理多个文件或者标准输入，而不必手动打开每个文件或者处理标准输入流。
## 主要功能和用法：

1. **逐行读取多个文件**：
   ```python
   import fileinput

   for line in fileinput.input(files=('file1.txt', 'file2.txt')):
       process(line)
   ```
   这段代码会依次读取 `file1.txt` 和 `file2.txt` 中的每一行，并对每一行进行处理。

2. **处理标准输入**：
   ```python
   import fileinput

   for line in fileinput.input():
       process(line)
   ```
   如果没有指定文件列表，`fileinput.input()` 将会从标准输入中读取数据。这在需要从管道或者重定向中读取数据时非常有用。

3. **获取当前文件名和行号**：
   ```python
   import fileinput

   for line in fileinput.input():
       print(fileinput.filename(), fileinput.filelineno(), line)
   ```
   `fileinput.filename()` 返回当前正在处理的文件名，`fileinput.filelineno()` 返回当前行的行号。

4. **命令行参数处理**：
   `fileinput` 还支持处理命令行参数，可以在命令行直接指定要处理的文件：
   ```bash
   python script.py file1.txt file2.txt
   ```
   在 `script.py` 中使用 `fileinput.input()` 将会依次处理 `file1.txt` 和 `file2.txt` 中的内容。

5. **自动关闭文件**：
   `fileinput` 会自动处理文件的打开和关闭操作，使得代码更加简洁和可读，同时避免了忘记关闭文件导致的资源泄漏问题。

总之，`fileinput` 模块提供了一种简便的方式来处理多个文件或者标准输入流，适合需要逐行处理多个文件内容的场景。

# 例
```Python
import fileinput

TEMPLATE = '''
     AAAAAAAAA
    FF       BB
    FF       BB
    FF       BB
    FF       BB
     GGGGGGGG
   EE       CC
   EE       CC
   EE       CC
   EE       CC
    DDDDDDDDD
'''

# These are ANSI Escape Codes
CLEAR = '\033[2J\033[1;1f'  # Clear screen and move cursor to top-left
WHITE = '\033[37m░\033[0m'  # A white block
BLACK = '\033[31m█\033[0m'  # A black block

for line in fileinput.input():
    # Execute the input line (like "A=0; B=1; ...") as Python code; the
    # variables A, B, ... will be stored in ctx.
    exec(line, (ctx := {}))
    
    # Initialize the display with a clear screen and the template.
    disp = CLEAR + TEMPLATE

    for ch in 'ABCDEFG':
        # Determine the block color.
        block = {
            0: WHITE,
            1: BLACK,
        }.get(ctx.get(ch, 0), '?')

        # Replace each character in the template with its block.
        disp = disp.replace(ch, block)

    print(disp)
```
## 解释
### `exec(line, (ctx := {}))`
- 这段代码尝试执行变量 `line` 中的内容，并使用空字典 `ctx` 作为局部上下文。
1. **`ctx := {}`**: 这是 Python 3.8 引入的海象运算符 (`:=`)。它将一个空字典 `{}` 赋值给 `ctx`，并返回 `ctx`。因此，`ctx` 变量现在是一个空字典。
2. **`exec(line, ctx)`**: `exec` 函数用于执行以字符串形式表示的 Python 代码 (`line`)。第二个参数 (`ctx` 在这里) 指定了代码执行时的局部命名空间。
   - `line`: 这应该是包含有效 Python 代码的字符串。
   - `ctx`: 这是执行代码时的局部命名空间，即其中定义的变量和函数会存在的地方。
#### 示例用法：
假设 `line` 包含一个或多个 Python 语句：
```python
line = "a = 10\nprint(a)"
exec(line, (ctx := {}))
print(ctx)  # 输出: {'a': 10}
```
在这个示例中：
- `line` 是 `"a = 10\nprint(a)"`，它首先将 `10` 赋给变量 `a`，然后打印 `a` 的值。
- `exec(line, (ctx := {}))` 执行了 `line` 中的代码，并在一个空字典 `{}` 的上下文中执行。
- 执行完成后，`ctx` 将包含 `{'a': 10}`，因为 `a` 是在局部上下文中定义的。
### `:=`
- 海象运算符 `:=` 是在 Python 3.8 版本中引入的新特性。它的作用是将表达式的值赋给变量，并且在表达式中可以直接使用该变量。这种功能通常用于在表达式中同时进行赋值操作。
- 例如，使用海象运算符可以简化代码并改善可读性，特别是在需要在条件语句或循环中重复使用同一个表达式结果时非常有用。
```python
# 使用传统的方式计算某个变量的平方并打印
x = 5
squared = x * x
print(squared)

# 使用海象运算符进行相同的操作
x = 5
print(squared := x * x)
```
- 在这个例子中，`squared := x * x` 将计算 `x` 的平方并将结果赋给 `squared` 变量，同时也打印出这个结果。
### block = {0: WHITE,1: BLACK,}.get(ctx.get(ch, 0), '?')
这行代码是一个字典操作，它有两个部分组成：
```python
block = {
    0: WHITE,
    1: BLACK,
}.get(ctx.get(ch, 0), '?')
```
1. **字典定义**:
   ```python
   {
       0: WHITE,
       1: BLACK,
   }
   ```
   这个字典定义了两个键值对：
   - 键 `0` 对应的值是 `WHITE`，代表白色块的 ANSI 转义码。
   - 键 `1` 对应的值是 `BLACK`，代表黑色块的 ANSI 转义码。
   这里的 `WHITE` 和 `BLACK` 是之前定义的 ANSI 转义码。
2. **字典的 `.get()` 方法**:
   在字典中使用 `.get()` 方法来获取指定键的值，如果键不存在，则返回默认值。
   ```python
   .get(ctx.get(ch, 0), '?')
   ```
   - `ctx.get(ch, 0)`：首先从字典 `ctx` 中获取键 `ch` 对应的值，如果键 `ch` 不存在，则返回默认值 `0`。
   - `.get(..., '?')`：然后再从前面定义的字典中获取上一步得到的值对应的内容。如果这个值不在 `0` 或 `1` 中，则使用 `'?'` 作为默认值。
   综合起来，这行代码的目的是根据变量 `ctx` 中的值（期望是 `0` 或 `1`），选择并返回相应的 ANSI 转义码，如果 `ctx` 中的值不是 `0` 或 `1`，则返回 `'?'`。