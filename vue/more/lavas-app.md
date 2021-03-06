# 将 PWA 站点打包成 App

Lavas 提供了将 PWA 站点打包成安卓 App 的功能，欢迎 [前往体验](https://lavas.baidu.com/app)。

## 背景

由于国内操作系统和浏览器对于 PWA 支持的情况并不乐观，导致可能 PWA 这项技术还是很难被用户所感知到，很多安卓手机需要进行比较麻烦的设置才能在某一些少量的浏览器上打开 `添加到桌面` 的入口，而且只有少量的浏览器支持 Service Worker。在这种市场环境下，很难有简便的方式将好用的 PWA 体验交给用户去使用。

然而 Lavas 转变了一下思路，可以将 PWA 的站点进行一次封装打包，打包成一个安卓的 App，并且 App 内置支持 PWA 特性的浏览器内核，这样就可以在 PWA 站点中引导用户安装打包后的 App, App 安装成功后，用户就可以通过安装后桌面上的 App icon 直接进入 PWA 站点，这样就能够突破操作系统和浏览器的限制将 PWA 的体验带给用户使用。

## 打包教程

打包的过程分为几个步骤，每一个步骤都有一些注意事项。

### 提供 PWA 站点

提供的 PWA 站点需要满足以下几个条件

- https 协议的 URL
- PWA 的 [lighthouse](https://lavas.baidu.com/guide/vue/doc/vue/more/check-your-pwa-websit#Lighthouse) 评分 70 分以上
- 站点首屏渲染时间较短（Lavas App 暂时没有做具体限制）

### 提供 email

email 作为 Lavas App 打包的沟通工具，用于后续接收打包结果，开发者在填写 email 的时候请选择常用的邮箱。

### 指定 App 名称

App 的名称为用户安装完 App 后的在桌面显示的名称，可以为中文或者英文。此名称不宜太长，一经确定，后续更新 App 的打包操作中，不宜修改。

### 指定应用包名

应用包名为 Lavas App 打包生成的 apk 名称，应用包名和密钥的生成有关，如果应用包名发生变化，则密钥验证会失败，所以当应用包名首次确定后，在后续的版本升级中不可修改。

应用包名的规则是 `lavas.xxx.xxx ...`

### 指定版本号

版本号为 Lavas App 的升级依据，当发布新版的 App 时，必须要求版本号比老版的 App 的版本号大，否则用户在安装 Lavas App 的时候可能会导致版本错误而安装不成功。

### 指定版本名称

版本名称即为标识当前的 App 的版本信息，通常和版本号保持大版本一致。

### App 密钥 & 密钥码

App 密钥是在 App 签名发布时的重要凭证。而密码是生成密钥和验证密钥的唯一凭证，打包成功后会在邮件中通知，请妥善保管。

- 首次打包 App 不需要上传 App 密钥
- 首次打包成功后，会在邮件中接收到一个 App 密钥连接，下载后妥善保存。
- 后续 App 升级必须上传密钥（不然用户在安装时会不会覆盖前面的版本的 App 导致安装失败）
- 密钥要求升级的 App 的 `应用包名` 和 `密钥码` 与之前首次打包保持一致，如果不一致，密钥将失效，用户将不能成功安装升级后的 App。

### App Logo

App Logo 是一张 PNG 图片，要求为正方形图片，512 * 512 大小以内的图片，将应用于 App 打开动画和 icon 的图片。

### 打包成功

App 打包完成后，可以在任何安卓手机上安装，并具备 PWA 特性。具体引导用户在不支持 PWA 的浏览器中去下载 PWA App 的策略可以自行设计。

## 注意事项

- Lavas App 当前为试用阶段，开发者需要自己线下维护 App 版本。
- 为了 App 的体验，需要保证 PWA 站点的质量。
- 反馈问题: 请邮件联系 lavas@baidu.com 或者 QQ 群反馈，群号：655433298