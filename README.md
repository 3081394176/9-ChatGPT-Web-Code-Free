# 某9-未编译源码-ChatGPT-Web-可商用

某9演示站: https://ai.jiangly.com

必要环境
nodejs version > 16
pnpm version > 6
mysql version >= 5.7
redis
目录结构
chat 用户端代码
admin 管理端代码
service 服务端代码
本地开发
三端统一命令

pnpm install 安装依赖

pnpm dev  启动项目

pnpm build 打包项目
启动项目
分别安装依赖 pnpm i
首先启动服务端进入service 创建.env文件 在其中修改 测试数据库信息和redis 配置完成后 pnpm dev
数据库通过orm映射 启动项目会自动创建数据库
启动完成后可以打开chat admin pnpm dev启动
关于授权
授权模块在 src/modules/globalConfig/globalConfig.service.ts 文件下
对函数 nineAiCheckAuth 移除其中内容就并且移除onModuleInit的nineAiCheckAuth就可以移除授权
对应的 src/modules/task/task.service.ts中的定时任务也可以移除掉 checkauth 定时任务
打包路径问题
service
后端服务直接 pnpm build 即可 .env为环境变量文件 需要后续自己挂载或者创建 项目有 示例文件.env.example
打包命令会对代码混淆，打包之后 只需要下图这些文件即可、其他文件不再需要


后端服务打包后需要这七个文件

chat
前端项目打包的配置文件是.env.production 和admin相同

只需要改变这个变量 如果分开部署的则填写你的线上后端服务地址 建议分开 第一行地址填写这个自己的线上地址就行

admin
管理端是同理、一样修改这个文件

同样分离部署只需要打开红框的内容即可、替换为自己的线上地址 其余配置并不需要修改 也暂时用不到

###其他文件

刷新404问题
前端history项目刷新都会404 需要对nginx进行配置
