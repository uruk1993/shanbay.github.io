# 项目结构

## 约定优于配置

你并不是唯一美丽的雪花。如果能放弃那些毫无意义的个人喜好，你就可以跳出诸多无谓选择的牢笼，在那些真正重要的领域快速前进。

有谁会在乎你的数据库主键采用什么格式吗？选择 id，postId，posts_id 或 pid 真的那么重要吗？这真的值得反复讨论才做出决定吗？当然不。

约定优于配置，不仅可以让我们避免许多无谓的思考，而且为更深层的抽象提供了肥沃的土壤。优良约定的威力就在于：每个广泛使用它们的领域都会受益颇丰。

`Sea` 正是遵循“约定优于配置”

## 项目目录结构

每个 `Sea` 项目都有固定的目录结构，特定的功能实现置于特定的 module 中。下面是一个最基本的 `Sea` 项目的目录结构

```
.
├── app
│   ├── extensions.py
│   ├── __init__.py
│   ├── servicers.py
├── configs
│   ├── default
│   │   ├── __init__.py
│   ├── development
│   │   └── __init__.py
│   ├── __init__.py
│   └── testing
│       └── __init__.py
├── jobs
│   └── __init__.py
├── protos
├── requirements.txt
└── tests
    └── __init__.py
```

### app

`app` 目录中包含项目的主体代码，其中最核心的是 `__init__.py`, `extensions.py`, `servicers.py`

> `__init__.py`:

定义了一个继承自 `sea.app.BaseApp` 的类： `App`

可以通过覆盖父类的方法，覆盖 `App` 的行为，也可以通过实现 `hook` 方法，定制初始化过程，例如定义 `ready` 方法，该方法会在`App` 初始化完成后执行。

关于 `sea.app.BaseApp` 的详细接口，请参见文档：[App](app)

> `extensions.py`:

声明了项目需要的 "扩展"，`sea` 支持通过 "扩展" 的方式来集成第三方的库，例如 orm, cache 等等。
每个扩展往往包括一个主类和需要的相应的配置，在 `extensions.py`中实力化这个类，并在项目中设置好这些配置，就可以使用了。

以内建的 `Cache` 为例：

`extensions.py`

```python
from sea.contrib.extensions.cache import Cache
cache = Cache()
```

使用方法一：

```python
from sea import current_app
current_app.extensions['cache']
```

使用方法二：

```python
from app.extensions import cache
```

关于 extension 的更多内容，请参见文档：[扩展](extension)

> `servicers.py`:

定义了 GRPC 的 Service

### configs

### jobs

### protos

### tests
