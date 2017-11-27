# 命令系统

### 如何编写和运行命令

有时候为了执行一些操作，需要写一些命令，例如数据迁移。
为 sea 的项目编写命令是非常简单的。


例如要创建一个 `print` 命令，接受一个可选参数 '-d/--date'，默认值是 2017-11-11'， 一个位置参数 'content'

则可以在项目根目录下的 `jobs/__init__.py` 中加入以下代码

```python
from sea.cli import jobm

@jobm.job('print')
@jobm.option('-d', '--date', default='2017-11-11')
@jobm.option('content')
def f1(date, content):
    print(content, 'at', date)
    return 0
```

这时候在命令行中可以得到如下效果

```sh
$ sea print -d 2017-12-12 Hello
Hello at 2017-12-12
```

**`@jobm.option(*args, **kwargs)`**

`*args` 和 `**kwargs`: 同 [argparse.ArgumentParser.add_argument](https://docs.python.org/3/library/argparse.html#the-add-argument-method)

**`@jobm.job(name, inapp=True, env='development', proxy=False, *args, **kwargs)`**

`name`: 命令的名称，例如上例中的 name 为 'print'，可以在命令中通过 `sea print` 来执行

`inapp`: 是否需实例化一个 [app](app)，如果需要，该命令需要在项目根目录下执行，默认为`True`

`env`: `SEA_ENV` 环境变量的默认值

`proxy`: 是否为一个转发命令, 默认 `False`。所谓转发命令，就是执行函数会接收一个额外参数 `argv`，其值为命令中传入的 `@jobm.option` 中未定义的参数的列表。例如

```python
@jobm.job('print', proxy=True)
@jobm.option('-d', '--date', default='2017-11-11')
def f1(date, argv):
    print(*argv, 'at', date)
    return 0
```

则效果如下：
```
$ sea print Hello World
Hello World at 2017-11-11
```

`*args` 和 `**kwargs`: 同 [argparse.ArgumentParser](https://docs.python.org/3/library/argparse.html#argparse.ArgumentParser)


### 内置的命令

### 第三方库中的命令

### 项目中的命令
