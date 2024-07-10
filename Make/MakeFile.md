---
date: 2024-07-09
aliases:
  - Make
tags:
  - Computer
  - MakeFile
---
# 什么是Makefile
- 一个 **Makefile** 是一个文本文件，通常用于在计算机程序开发中自动化编译和构建项目。它包含了一系列的规则（rules），告诉编译器如何编译和链接源代码文件以生成最终的可执行文件、库文件或者其他目标文件。
- 主要作用和特点包括：
	1. **自动化编译和构建**：Makefile 通过定义依赖关系，可以让编译器（如 GNU make）根据文件之间的依赖关系，自动进行编译和链接，避免手动输入复杂的编译指令。
	2. **规则和目标**：Makefile 中包含了多个规则，每个规则定义了一个或多个目标文件、依赖文件以及生成目标的命令。例如，一个简单的规则可以是：如果源文件修改了，那么需要重新编译生成对应的目标文件。
	3. **变量和宏定义**：Makefile 支持变量定义和宏定义，可以用来简化和通用化编译过程中的参数传递和路径设置。
	4. **条件编译**：Makefile 支持条件语句，可以根据不同的条件执行不同的编译或者链接过程，例如针对不同的操作系统平台或者不同的编译选项。
	5. **清理和维护**：Makefile 中通常也包含了清理（clean）规则，用于删除生成的中间文件或者目标文件，以及维护（maintenance）规则，用于备份或者检查代码。
- Makefile 的格式通常使用一种类似于命令行的语法，具体规则的书写和语法可以根据具体的项目和编译环境有所不同，但是其基本的作用是为了自动化地管理和构建复杂的软件项目。
# 为什么要用make
- 自动化
	- 只需要写一个Makefile，就可以通过一句命令来自动化的完成编译、测试、打包、部署等一系列操作
- 可以用来执行任何命令
# 如何编写MakeFile
- 用于指定构建或执行某个目标的步骤和依赖关系
```makefille
target ... : prerequisites ...
	command
	...
	...
```
- 目标`target`：这是希望创建或执行的文件、动作或操作的名称。在命令行上输入该名称通常会触发相关的操作。
	- `.PHONY` 定义伪目标
```makefile
.PHONY: clean
```
- 先决条件`prerequisites`：这些是目标的依赖项，也就是使得目标被视为最新状态所需的条件。如果任何一个先决条件的修改时间比目标文件的修改时间要新，那么接下来的命令就会被执行以更新目标。
- 命令`command`：这是用于创建或更新目标的实际命令或操作步骤。这些命令可以是编译命令、文件复制操作或其他任何必要的操作。
	- 即触发 target 时执行的 shell 命令
	- 开头加 `@` 不会在终端输出命令本身
	- 开头加 `-` 会忽略命令执行失败的错误，继续向下执行
- 例如：
```makefile
output.txt: input.txt
    cp input.txt output.txt
    echo "File copied successfully!"

```
- 这个 Makefile 片段的作用是，如果 `input.txt` 的修改时间比 `output.txt` 新，那么会执行 `cp input.txt output.txt` 命令来将 `input.txt` 复制到 `output.txt`，然后输出 "File copied successfully!"。
# Makefile变量
在 Makefile 中，`=`, `:=`, `?=` 和 `+=` 是用来定义变量的不同方式，它们的使用方式和行为有所不同：
1. **`=`**: 简单赋值
   - 使用 `=` 进行赋值时，变量会被**延迟展开**，也就是在使用变量时才会被展开。
   - 示例：
     ```makefile
     VAR = value
     TARGET = $(VAR)
     VAR = new_value
     ```
     在这个例子中，`TARGET` 最终的值是 `new_value`，因为 `VAR` 在 `TARGET` 被使用时才被展开。

2. **`:=`**: 立即赋值
   - 使用 `:=` 进行赋值时，变量会被**立即展开**，也就是在赋值时就被展开。
   - 示例：
     ```makefile
     VAR := value
     TARGET := $(VAR)
     VAR := new_value
     ```
     在这个例子中，`TARGET` 的值是 `value`，因为 `VAR` 在 `TARGET` 赋值时已经被展开为 `value`。

3. **`?=`**: 条件赋值
   - 使用 `?=` 时，只有在变量未定义时才会进行赋值。
   - 示例：
     ```makefile
     VAR ?= value
     TARGET := $(VAR)
     ```
     如果之前没有定义 `VAR`，那么 `VAR` 的值将会是 `value`。

4. **`+=`**: 追加赋值
   - 使用 `+=` 可以在已有变量的值后面追加内容，类似于字符串的拼接。
   - 示例：
     ```makefile
     SOURCES := file1.c
     SOURCES += file2.c
     ```
     最终 `SOURCES` 的值是 `file1.c file2.c`。

## 示例说明

考虑以下示例来理解这些赋值方式的区别：

```makefile
# 使用不同的赋值方式定义变量
VAR = initial_value
TARGET1 = $(VAR)
VAR = new_value
TARGET2 := $(VAR)
VAR ?= default_value
TARGET3 := $(VAR)
SOURCES := file1.c
SOURCES += file2.c

all:
    @echo "TARGET1: $(TARGET1)"
    @echo "TARGET2: $(TARGET2)"
    @echo "TARGET3: $(TARGET3)"
    @echo "SOURCES: $(SOURCES)"
```

在这个 Makefile 中：
- `TARGET1` 的值是 `new_value`，因为使用了延迟展开的 `=` 赋值方式。
- `TARGET2` 的值是 `initial_value`，因为使用了立即展开的 `:=` 赋值方式。
- `TARGET3` 的值是 `initial_value`，因为 `VAR` 已经被定义，所以 `?=` 不会改变它的值。
- `SOURCES` 最终的值是 `file1.c file2.c`，因为使用了 `+=` 追加赋值方式。

这些赋值方式的选择通常取决于需要在何时展开变量，以及是否需要在变量已经定义时进行重新赋值或追加操作。
## 变量引用
- $(VAR)：引用变量 VAR（MakeFile 中的变量引用）
- ${VAR}：引用变量 VAR（Shell 中的变量引用）
- 可以通过`$(shell command)`来将 command 的输出结果作为替换的值
- 可以直接使用环境变量，如`$(PATH)`
# make命令
- make 后面可以跟多个 target，指定执行的内容
	- 如果不跟任何 target，则默认执行第一个 target
- 可以在 make 后面直接通过 `VAR=value`的形式来定义变量
	- 优先级：make后 > Makefile 中定义 > 环境变量（make 前）
- 一些常用的 make 命令 flag：
	- make -f FILE：指定 Makefile 文件
	- make -n：不执行命令，只显示命令
	- make -s：不显示命令
	- make -j N：并行执行 N 个任务
	- make -k：忽略错误，继续执行
# more
## 条件判断
## 函数
## . . .
# 可能问题
- `make: *** No targets specified and no makefile found. Stop.`
	- 文件名是 Makefile 或 makefile，而不是MakeFile