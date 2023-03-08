---
title: 從零開始的Python
date: 2023-03-08 20:19:16
tags: python
---

## Python 是什麼？

Python 是一種高級程式語言，它非常流行，並且適合新手學習。Python 被廣泛用於數據科學、機器學習、人工智慧、Web 開發等領域。

Python 有許多優點，包括：

* 容易上手：Python 語法簡潔，易於理解和學習。
* 多用途：Python 可以用於各種不同的任務，從簡單的腳本到大型的應用程式。
* 開源：Python 是一個開源的語言，這意味著您可以免費使用和修改它。

## 安裝 Python

在開始使用 Python 之前，您需要先安裝Python。可以通過以下步驟在您的計算機上安裝 Python：

1. 前往 Python 官方網站：https://www.python.org/downloads/
2. 下載最新版本的 Python。
3. 運行安裝程序，按照提示進行安裝。

## 編寫您的第一個 Python 程式

在您安裝完 Python 之後，讓我們來編寫一個簡單的 Python 程式來確認一下。打開您的編輯器，創建一個新文件，並將以下代碼複製貼上到文件中：

```py
print("Hello, world!")
```

接下來，將文件存為 hello.py，並在cmd或其他命令行界面中運行這個指令：

```shell
python hello.py
```

您應該會在命令行中看到 "Hello, world!"。

## Python 基礎

現在讓我們來了解一下 Python 的一些基本概念。

### 變數

變數是一個記憶體位置，用於存儲值。您可以通過向變數賦值來創建變數。例如：

```py
x = 5
y = "Hello"
```

在此範例中，我們創建了兩個變數：一個整數變數 `x` 和一個字符串變數 `y`。

### 數據類型

Python 支持多種不同的數據類型，包括整數、浮點數、字符串和布林值。您可以使用 `type()` 方法來檢查變數的數據類型。例如：

```py
x = 5
y = 3.14
z = "Hello"
w = True

print(type(x))
print(type(y))
print(type(z))
print(type(w))
```

在這個例子中，我們建立了四個變數，每個變數都是不同的數據類型。type() 方法用於檢查每個變數的數據類型。

### 字符串

```py
x = "Hello"
y = 'World'
```

您可以使用加號（+）運算符將兩個字符串連接在一起。例如：

```py
z = x + y
print(z)
```

這將輸出 `"HelloWorld"`。

您還可以使用大括號（{}）和 format() 方法來格式化字串。例如：

```py
age = 25
txt = "My name is John, and I am {} years old"
print(txt.format(age))
```

這會印出 "My name is John, and I am 25 years old"。

### 列表

列表是一個有序的元素集合。您可以使用方括號（[]）定義一個列表，並使用逗號分隔列表中的元素。例如：

```py
fruits = ["apple", "banana", "cherry"]
```

您可以通過索引（從 0 開始）訪問列表中的元素。例如：

```py
print(fruits[0])
```

這會輸出 3。

### 條件語句

條件語句用於根據特定條件執行不同的操作。在 Python 中，使用 if 關鍵字定義一個條件語句。例如：

```py
x = 5
if x > 0:
    print("x is positive")
```

在這個例子中，如果 x 大於 0，則輸出 "x is positive"。

您可以使用 elif 和 else 關鍵字來添加其他條件。例如：

```py
x = 0
if x > 0:
    print("x is positive")
elif x == 0:
    print("x is zero")
else:
    print("x is negative")
```

在這個例子中，如果 x 大於 0，則輸出 "x is positive"；如果 x 等於 0，則輸出 "x is zero"；否則，輸出 "x is negative"。

### 循環

循環用於重複執行相同的代碼塊。在 Python 中，有兩種類型的循環：`for` 循環和 `while` 循環。

#### for 循環

`for` 循環用於遍歷序列（如列表、元組、字符串等）中的元素。例如：

```py
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
    print(fruit)
```

這將輸出 "apple"、"banana" 和 "cherry"。

您可以使用 `range()` 方法生成一個數字序列，然後在循環中使用它。例如：

```py
for x in range(3):
    print(x)
```

這將輸出 0、1 和 2。

#### while 循環

`while` 循環用於在條件為真時重複執行代碼塊。例如：

```py
x = 0
while x < 3:
    print(x)
    x += 1
```

這將輸出 0、1 和 2。

在 while 循環中，您需要謹慎處理條件，以避免出現無限循環的情況。

### 函數

函數是一個獨立的代碼塊，可以執行特定的任務。在 Python 中，使用 `def` 關鍵字定義一個函數。例如：

```py
def my_function(name):
    print("Hello, " + name)

my_function("John")
```

這將輸出 "Hello, John"。

在函數中，您可以使用 `return` 關鍵字返回一個值。例如：

```py
def square(x):
    return x * x

result = square(5)
print(result)
```

這將輸出 25。

## 小結

這是一個簡單的 Python 入門指南，介紹了 Python 的基本概念，如變量、數據類型、字符串、列表、條件語句、循環和函數。熟悉這些基本概念是學習 Python 編程的第一步。
