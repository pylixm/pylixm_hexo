---
layout : post
title : 「python 技巧」译-python 3 值得尝试的技巧
categories: [Python,] 
date : 2019-05-16
url: /posts/2019-05-16-python-trick.html 
tags : [Python,]
---

> 标题：Things you’re probably not using in Python 3 – but should 
> 原文：https://datawhatnow.com/things-you-are-probably-not-using-in-python-3-but-should/
> 作者：Vinko Kodžoman 
> 时间：May 6, 2019
> 译者：DeanWu


在Python2的停止维护日期（[Python EOL](https://pythonclock.org/)）的发布之后，越来越多的人开始从python2转为python3。但是，我发现大多数Python3代码看起来还是想Python3。在我以前的博文（[Python web 抓取简介](https://datawhatnow.com/introduction-web-scraping-python/)）中的实例也是如此，我为此感到内疚。

下面，我将展示一些令人兴奋的功能实例，他们只能在Python3的环境下使用，他们可以帮助你更轻松的解决问题。

所有示例都是用Python 3.7编写的，每个实例都包含该功能所需的最低Python版本。

## f-strings（3.6+）

在任何编程语言中没有字符串都很难做任何事情，为了保持稳定，你希望有一种结构化的方式来处理字符串。大多数使用Python的人更喜欢使用`format`方法。

```python
user = "Jane Doe"
action = "buy"
log_message = 'User {} has logged in and did an action {}.'.format(
  user,
  action
)
print(log_message)
# User Jane Doe has logged in and did an action buy.
```

除`format`外，Python 3还提供了一种通过[f-string](https://www.python.org/dev/peps/pep-0498/)进行字符串插值的灵活方法。使用`f-strings`的上述代码如下所示：

```python
user = "Jane Doe"
action = "buy"
log_message = f'User {user} has logged in and did an action {action}.'
print(log_message)
# User Jane Doe has logged in and did an action buy.
```

## Pathlib（3.4+）

`f-strings`是惊人的，但是像文件路径这样的字符串有自己的库，这使得它们的操作更加容易。Python 3提供了`pathlib`作为处理文件路径的便捷抽象库。如果您不确定为什么要使用pathlib，请尝试阅读这篇优秀文章 - [为什么您应该使用pathlib](https://treyhunner.com/2018/12/why-you-should-be-using-pathlib/) - by [Trey Hunner](https://treyhunner.com/)。

```python
from pathlib import Path
root = Path('post_sub_folder')
print(root)
# post_sub_folder
path = root / 'happy_user'
# Make the path absolute
print(path.resolve())
# /home/weenkus/Workspace/Projects/DataWhatNow-Codes/how_your_python3_should_look_like/post_sub_folder/happy_user
```

## Type hinting (类型注解) (3.5+)

静态与动态类型是软件工程中的一个热门话题，几乎每个人都对它有自己的看法。我会让读者决定何时应该编写类型，但我认为你至少应该知道Python 3支持[type hints](https://docs.python.org/3/library/typing.html)。

```python
def sentence_has_animal(sentence: str) -> bool:
  return "animal" in sentence
sentence_has_animal("Donald had a farm without animals")
# True
```

## Enumerations（枚举） (3.4+)

Python 3支持一种简单方法可通过编写Enum类来实现枚举。枚举是一种封装常量列表的便捷方式，因此它们不会随机分布在整个代码中而没有太多结构。

```python
from enum import Enum, auto
class Monster(Enum):
    ZOMBIE = auto()
    WARRIOR = auto()
    BEAR = auto()
    
print(Monster.ZOMBIE)
# Monster.ZOMBIE
```

>An enumeration is a set of symbolic names (members) bound to unique, constant values. Within an enumeration, the members can be compared by identity, and the enumeration itself can be iterated over.
>枚举是一组绑定到唯一常量值的符号名称(成员)。在枚举中，可以通过标识来比较成员，并且可以迭代枚举本身。 
>https://docs.python.org/3/library/enum.html

```python
for monster in Monster:
    print(monster)
# Monster.ZOMBIE
# Monster.WARRIOR
# Monster.BEAR
```

## Built-in LRU cache（内建LRU缓存） (3.2+)

我们今天使用的软件和硬件，在很多地方都使用了高速缓存。Python 3通过将LRU（[最近最少使用](https://en.wikipedia.org/wiki/Cache_replacement_policies#Least_recently_used_(LRU))）缓存暴露为名为`lru_cache`的装饰器，使得使用它们变得非常简单。

下面是一个简单的`Fibonacci`函数，他多次递归都执行相同的逻辑，我们可以使用缓存来优化它。

```python
import time

def fib(number: int) -> int:
    if number == 0: return 0
    if number == 1: return 1
    return fib(number-1) + fib(number-2)

start = time.time()
fib(40)
print(f'Duration: {time.time() - start}s')
# Duration: 30.684099674224854s
```

现在我们可以使用它`lru_cache`来优化它（这种优化技术称为[memoization](https://en.wikipedia.org/wiki/Memoization)）。执行时间从几秒到几纳秒。

```python
from functools import lru_cache
@lru_cache(maxsize=512)
def fib_memoization(number: int) -> int:
    if number == 0: return 0
    if number == 1: return 1
    
    return fib_memoization(number-1) + fib_memoization(number-2)
start = time.time()
fib_memoization(40)
print(f'Duration: {time.time() - start}s')
# Duration: 6.866455078125e-05s
```

## Extended iterable unpacking （可迭代对象的扩展使用）(3.0+)

可直接在这里查看代码说明 [docs](https://www.python.org/dev/peps/pep-3132/)

```python
head, *body, tail = range(5)
print(head, body, tail)
# 0 [1, 2, 3] 4
py, filename, *cmds = "python3.7 script.py -n 5 -l 15".split()
print(py)
print(filename)
print(cmds)
# python3.7
# script.py
# ['-n', '5', '-l', '15']
first, _, third, *_ = range(10)
print(first, third)
# 0 2
```

## Data classes (3.7+)

Python 3引入了 [data class](https://docs.python.org/3/library/dataclasses.html)，这些数据类没有很多限制，可用于减少样板代码，因为装饰器会自动生成特殊方法，例如__init__()和__repr()__。从官方[提案](https://www.python.org/dev/peps/pep-0557/)中，它们被描述为“具有默认值的可变命名元组”。

```python
class Armor:
    
    def __init__(self, armor: float, description: str, level: int = 1):
        self.armor = armor
        self.level = level
        self.description = description
                 
    def power(self) -> float:
        return self.armor * self.level
    
armor = Armor(5.2, "Common armor.", 2)
armor.power()
# 10.4
print(armor)
# <__main__.Armor object at 0x7fc4800e2cf8>
```

使用`data class`来实现 `Armor`:

```python
from dataclasses import dataclass
@dataclass
class Armor:
    armor: float
    description: str
    level: int = 1
    
    def power(self) -> float:
        return self.armor * self.level
    
armor = Armor(5.2, "Common armor.", 2)
armor.power()
# 10.4
print(armor)
# Armor(armor=5.2, description='Common armor.', level=2)
```

## 总结

想互联网上的其他教程列表一样，本列表并不完整。我希望这篇文章向您展示了至少一个您以前不知道的Python 3功能，并且它将帮助您编写更清晰，更直观的代码。
