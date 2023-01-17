**_Visual Studio Code 预览文档：快捷键 Ctrl + K , V 或 Ctrl + Shift + V_**

## 编辑环境

### 安装软件

- 下载 [Hugo](https://github.com/gohugoio/hugo/releases)

- 下载 [Git](https://git-scm.com/downloads)

- 下载 [Visual Studio Code](https://code.visualstudio.com/download)

### 安装 Visual Studio Code 扩展

**必装：格式化、Markdown 语法提示**

1. Prettier：格式化

2. Markdown All in One：提示 markdown 语法

_选装_

1. File Peek：跳转定义

2. Git History：查看 Git 提交历史记录

3. GitLens：鼠标光标聚焦的代码行，行右侧将显示上一次提交信息

4. Markdown PDF：将 md 文件转为 pdf 文件

5. Path Autocomplete：自动补全引用路径

### 自定义 Visual Studio Code 配置

- 查看 .vscode/settings.json，若置灰，则表示未安装扩展，配置无效

## 本地预览

1. 启动服务

   ```sh
   hugo serve
   ```

2. 打开浏览器，访问：http://localhost:1313

## 创作内容

### 图文分享

1. 创建文件，执行如下命令：

   ```sh
   hugo new projects/你的图文名称/index.md
   ```

2. 使用 markdown 语法编写

### 编写博客

1. 创建文件，执行如下命令：

   ```sh
   hugo new blog/你的博客标题.md
   ```

2. 使用 markdown 语法编写

## 发布网站

1. 首次使用需追加仓库

   ```sh
   git remote set-url --add origin https://git.soarch.top/c1302/webspace.git
   ```

   账号密码请联系管理员

2. 修改版本号，打开 docker-compose.yml 文件，内容如下：

   ```yml
   version: '3'
   services:
   soarch_hugo:
     image: registry.cn-hangzhou.aliyuncs.com/soarch/c1302:1.0.0 # 修改此行
     container_name: 'c1302'
     ports:
       - '5004:80'
     restart: always
   ```

   版本号分为 3 位数字，由小数点间隔

   - 第 1 位版本号：数字为 1，暂时固定不变

   - 第 2 位版本号：换主题，则数字加 1，将第三位版本号归零

   - 第 3 位版本号：每次发布加 1

3. 提交更改内容，执行如下命令：

   ```sh
   git add .
   git commit -m "修改信息"
   git push
   ```

4. 打标签，执行如下命令：

   ```sh
   git tag -a 1.0.0 -m "修改信息概述" # 必须对应步骤1的版本号
   ```

5. 推送版本号，执行如下命令：

   ```sh
   git push origin 1.0.0 # 必须对应步骤1的版本号
   ```

6. 可联系管理员到 CI 平台查看流水线是否成功

## 其他注意事项

- 图片处理最大不超过 200K，再大则请学习使用图床
- 如需更换皮肤，请学习 Hugo
