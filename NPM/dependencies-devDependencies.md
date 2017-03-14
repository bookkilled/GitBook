# dependencies和devDependencies的区别
package.json 文件中两个属性：dependencies和devDependencies

一个node package有两种依赖，一种是dependencies一种是devDependencies，其中前者依赖的项该是正常运行该包时所需要的依赖项，而后者则是开发的时候需要的依赖项，像一些进行单元测试之类的包。

如果你将包下载下来在包的根目录里运行
```bash
npm install
```
默认会安装两种依赖，如果你只是单纯的使用这个包而不需要进行一些改动测试之类的，可以使用
```bash
npm install --production
```
只安装dependencies而不安装devDependencies。
如果你是通过以下命令进行安装
```bash
npm install packagename
```
那么只会安装dependencies，如果想要安装devDependencies，需要输入
```bash
npm install packagename --dev  
```
后面的webpack配置中，会遇到好多新版本的插件会有问题，安装时 需要对应修改依赖包的版本号。
