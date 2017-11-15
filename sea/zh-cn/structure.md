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

### `app`

`__init__.py`

`extensions.py`

`servicers.py`

### `configs`

### `jobs`

### `protos`

### `tests`
