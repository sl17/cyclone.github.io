---
published: true
---
关于npm install的几种关系

#### npm install X:

- 会把X包安装到`node_modules`目录中
- 不会修改`package.json`
- 之后运行`npm install`命令时，不会自动安装X

#### npm install X –save:

- 会把X包安装到`node_modules`目录中
- 会在`package.json`的`dependencies`属性下添加X
- 之后运行`npm install`命令时，会自动安装X到`node_modules`目录中
- 之后运行`npm install –production`或者注明`NODE_ENV`变量值为`production`时，会自动安装`msbuild`到`node_modules`目录中

 

#### npm install X –save-dev:

- 会把X包安装到`node_modules`目录中
- 会在`package.json`的`devDependencies`属性下添加X
- 之后运行`npm install`命令时，会自动安装X到`node_modules`目录中
- 之后运行`npm install –production`或者注明`NODE_ENV`变量值为`production`时，不会自动安装X到`node_modules`目录中

 

#### npm install X –g:

- 安装模块到全局，不会在项目`node_modules`目录中保存模块包。
- 不会将模块依赖写入`devDependencies`或`dependencies` 节点。
- 运行 `npm install` 初始化项目时不会下载模块。
- `npm install -g moduleName # -g` 的意思是将模块安装到全局，具体安装到磁盘哪个位置，要看 `npm config prefix` 的位置，具体查看方法是在终端输入`npm config edit`，在弹出的文档中找到; `prefix=C:\node`，就是了。


### 使用原则:

运行时需要用到的包使用`–save`，否则使用`–save-dev`。

 

### 主要区别

`devDependencies`中的包是在开发中用到的，而发布后是找不到，而`dependencies`中的包是开发和线上都需要用到的。我们在卸载某个包的时候也可以根据上面说的添上`–save`或`–save-dev` 就会在`package.json`中删除相应的配置。


### 总结

`devDependencies` 节点下的模块是我们在开发时需要用的，你写 ES6 代码，需要babel转换成es5，转换完成后，我们只需要转换后的代码，上线的时候，直接把转换后的代码部署上线，不需要`bebal`了，上线了不需要，这就是`devDependencies`，所以我们可以使用 `-save-dev` 的形式安装。如果你用了 `jQuery`，由于发布之后还是依赖`jQuery`，所以是`dependencies`，所以我们应该使用 -`save` 的形式安装。
