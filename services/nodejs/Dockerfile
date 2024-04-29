# 使用 Node.js 官方镜像作为基础镜像
FROM ${NODE_VERSION}

# 安装 n（Node 版本管理器）
RUN npm install -g n

# 设置 n 的镜像源为淘宝 npm 镜像，加速 Node.js 版本的下载
RUN n config set registry https://registry.npm.taobao.org

# 安装 Node.js 版本，并设置为默认版本
RUN n ${NODE_VERSION}

# 安装 cnpm（淘宝 npm 镜像加速版 npm）
RUN npm install -g cnpm --registry=https://registry.npm.taobao.org

# 输出已安装的 Node.js 版本
RUN node --version

# 设置工作目录
WORKDIR /app

# 复制 package.json 和 package-lock.json 到容器中
COPY package*.json ./

# 安装项目依赖
RUN npm install

# 复制应用程序代码到容器中
COPY . .

# 运行应用程序
CMD ["node", "app.js"]
