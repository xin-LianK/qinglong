## 阿里云盘每日签到

> 基于 Node.js 实现的阿里云盘每日签到

### TODO

- [x] 阿里云盘签到
- [x] 青龙面板支持
- [ ] 本地运行
- [ ] ~~github action 支持~~

### Use 使用

#### 第一步：获取 refresh_token 并复制

- 自动获取: 登录[阿里云盘](https://www.aliyundrive.com/drive/)后，控制台粘贴
```javascript
copy(JSON.parse(localStorage.token).refresh_token); console.log(JSON.parse(localStorage.token).refresh_token);
```
`
  ![](./assets/refresh_token_1.png)

- 手动获取: 登录[阿里云盘](https://www.aliyundrive.com/drive/)后，可以在开发者工具 ->
  Application -> Local Storage 中的 `token` 字段中找到。  
  注意：不是复制整段 JSON 值，而是 JSON 里 `refresh_token` 字段的值，如下图所示红色部分：
  ![refresh token](./assets/refresh_token_2.png)

#### 第二步：青龙面板添加依赖项

- axios

#### 第三步：添加环境变量

> `CLIENT_ID` 需添加 `环境变量` 权限

| 参数          | 说明                                             |
| ------------- | ------------------------------------------------ |
| refreshToken  | 阿里云盘 refresh_token, 添加多个可支持多账户签到 |
| CLIENT_ID     | 可选项, 用于青龙面板 API 更新 refreshToken 字段  |
| CLIENT_SECRET | 可选项, 用于青龙面板 API 更新 refreshToken 字段  |
| QL_PATH       | 可选项, 青龙面板path                            |

`CLIENT_ID` 和 `CLIENT_SECRET` 可在 `青龙面板 -> 系统设置 -> 应用设置 -> 新建应用` 新增, 用于自动更新环境变量内 `refreshToken` 配置

#### 第四步：添加订阅

> 添加订阅后可在定时任务列表发现新增任务, 可自行调整任务执行时间
```shell
ql repo https://github.com/mrabit/aliyundriveDailyCheck.git "autoSignin" "" "qlApi"
```

##### 新版本:

`青龙面板 -> 订阅管理 -> 新建订阅`, 在名称输入框粘贴命令并执行

##### 旧版本:

`青龙面板 -> 定时任务 -> 新建任务` 添加命令并执行

![aliyundriveDailyCheck.png](./assets/aliyundriveDailyCheck.png)

### 申明

- 本项目仅做学习交流, 禁止用于各种非法途径
- 项目中的所有内容均源于互联网, 仅限于小范围内学习参考, 如有侵权请第一时间联系 [本项目作者](https://github.com/mrabit) 进行删除

### 鸣谢

#### 特别感谢以下作者及所开发的程序，本项目参考过以下几位开发者代码及思想。

- @Anonym-w: [Anonym-w/autoSigninAliyun](https://github.com/Anonym-w/autoSigninAliyun)
- @ImYrS: [ImYrS/aliyun-auto-signin](https://github.com/ImYrS/aliyun-auto-signin)


# auto_comment

## JD自动评价

支持评价晒单（带两张图），追评，服务评价，支持AI生成评价内容

青龙拉库命令 ql repo https://github.com/6dylan6/auto_comment.git "jd_" "" "jdspider"

如果运行报依赖错误，运行评价依赖安装任务，没有问题不要运行

浏览器登录抓取CK（PC端CK），添加变量PC_COOKIE，每次运行评价10个订单

www的那个地址抓CK，登录后F12点到network，不要用命令document.cookie抓，会不完整，找带cookie的请求复制（其实只复制thor=xxx这串就行）

有问题欢迎提pr、issue

## 更新日志：

2022/11/6 新增多账号； 报错不停止运行；带两个图评价晒单；倒序评价，优先比较老的订单

2022/11/16 修复有些订单匹配不到pid；服务评价报错

2022/11/20 随机选取评价图片

2023/1/7 正常运行，有问题的多跑几次看看

2023/3/14 正常使用

2023/3/28 修复评价内容乱码

2023/4/19 添加gpt生成评价内容，当配置OPENAI_API_KEY环境变量启用，具体用法看注释（Cp0204的pr）

2023/4/22 移除openai依赖，优化代理方式，优化日志显示（Cp0204的pr）

2023/6/27 gpt错误跳出（Cp0204的pr）

2023/7/28 修复获取不到评价信息

2023/9/17 修复收集不到商品评价

## 运行例图（评价晒单基本是优质评价，评价有奖的订单可以获得奖励！！！）：

![image](https://i.postimg.cc/KznsXxfN/1.png)
