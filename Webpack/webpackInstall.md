# Webpack 学习笔记
## 什么是webpack？

## 打包配置
- 创建文件 Demo 并进入文件夹`cd Demo`
- 创建package.json文件`npm init` **注意：name属性值不允许大写字母**
- 为当前demo项目创建 webpack `npm install webpack --save-dev`
- 在demo文件夹下多了node\_modules文件夹
- 在package.json中多了有关webpack的配置
- 创建 .gitignore 忽略特殊文件上传  

  ```bash
  # My configurations:
  .Ulysses-Group.plist
  *.git
  .DS_Stroe
  .gitignore
  ```
- 安装依赖包
		npm install style-loader css-loader url-loader babel@5.8 babel-core@5.4.7 babel-loader@5.0.0 less-loader file-loader autoprefixer autoprefixer-loader html-webpack-plugin extract-text-webpack-plugin html-loader webpack-dev-server react@0.14 react-dom@0.14 --save-dev
- 独立出css样式
		`$ npm install extract-text-webpack-plugin --save-dev`
