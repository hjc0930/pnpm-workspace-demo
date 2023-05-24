# pnpm workspace

## 搭建

在项目父工程下创建 `pnpm-workspace.yaml`文件，里面声明需要加入workspace的目录

```yaml
packages:
  # all packages in direct subdirs of packages/
  - 'packages/*'
  # all packages in subdirs of components/
  - 'components/**'
  # exclude packages that are inside test directories
  - '!**/test/**'
```
初始化你的子项目工程，并添加`package.json`文件，修改文件中的 `name`(项目名)和`main`(项目入口文件)两个字段，**这关系到后面多个项目间互相引用依赖**

## 安装依赖

- 一次性安装父工程和子工程的所有依赖：`pnpm i`

- 安装依赖到父工程：`pnpm add <dependent name> -w`/`pnpm add <dependent name> -wD`

- 安装依赖到指定的子工程：`pnpm add <dependent name> -r --filter <project name>`

## 运行子工程命令

- 运行某个子工程命令：`pnpm run --filter <project name> <scripts name>`

## 子工程互相引用

子工程互相引用的前提是`package.json`中的`name`和`main`字段得配置好

- 在A工程中引用B工程：`pnpm add nameA -r --filter nameB`