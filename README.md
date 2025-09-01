简体中文 | [English](./README_EN.md)

> [!IMPORTANT]
> ## 致大家
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;嘿！恭喜你看到这里~ 这是酪灰基于原作者 imsyy 主页的修改版本！修改版本添加了更多的功能，但是也会带来更高的性能占用！（主要来自逐字歌词以及季节效果渲染），也添加了安全更新，增强安全性。<p>
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;酪灰作为 Vue 初学者，因为热爱，拉着同学 Pizero 完善了这个项目，因此这些代码可能会很 shi，并可能充斥着不少 BUG。欢迎在遇到 BUG 时进行反馈，也欢迎各位大佬帮助！<p>
>#### 关于问题反馈以及求助
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;遇到问题请在 Github 上提 issue ，需要帮助请在 Github 上发 discussion ，看到了会回复。除特殊情况外，<b>请不要直接通过其它社交方式联系酪灰！</b>酪灰不是客服，不提供售后服务，并没有那么多的时间来回复私聊。还请谅解！<p>
>### 最后，喜欢本项目的话麻烦给个 STAR ！阿里嘎多~

<p>&nbsp;<p>

> [!WARNING]
> ## 关于 PWA 缓存的问题
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;由于 PWA 依赖的 Workbox 组件已经<b>长达 1 年</b>没有发布新 Release ，导致 Workbox 仍在使用已经被弃用的 glob 版本 7.2.3 。这个问题造成项目在运行时提示包含弃用的依赖。 <p>
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;<b>So Google , fuck you !</b><p>
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;目前项目放弃对 PWA 缓存的支持，强制将 glob 覆盖到高版本。故编译时会得到错误 ：<p>
> ```bash
> PWA v1.0.3
>mode      generateSW
>precache  8 entries (0.00 KiB)
>files generated
>  dist/sw.js
>  dist/workbox-4523edd1.js
>warnings
>  An error occurred when globbing for files. 'Cannot read properties of undefined (reading 'sync')'
>
>✓ built in 13.21s
> ```
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;但除了缓存外并不会导致项目出现其它异常。如果需要启用这个功能，请删除 `package.json` 内`overrides`中的`"glob": "^11.0.3"`，然后重新执行`pnpm install`。此功能应该会恢复正常，<p>
>### So Google , fuck you !

<p>&nbsp;<p>
<strong><h2>無名の主页</h2></strong>
</p>

![無名の主页](/screenshots/main.png)<p>
![無名の主页](/screenshots/main1.png)<p>
![無名の主页](/screenshots/main2.png)<p>

### 👀 Demo

> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;由于 workbox 缓存原因，查看最新效果可能需要 `Ctrl` + `F5` 强制刷新浏览器缓存噢！

- [酪灰の主页](https://nanorocky.top/)

> 【小贴士】如果您的项目不需要 workbox 的本地缓存，比如有 CDN 的情况下，或者是遇到访问子路径自动跳转主页的情况，可以取消注释 `vite.config.ts` 内的两行代码：

```bash
selfDestroying: true,
injectRegister: false,
```

### 🎉 功能

- [x] 载入动画
- [x] 站点简介
- [x] Hitokoto 一言
- [x] 日期及时间
- [x] 实时天气
- [x] 时光进度条
- [x] 音乐播放器
- [x] 移动端适配
- [x] 逐字歌词兼容

### ⚙️ 自动部署

如果遇到构建环境或者打包过程出现错误，则可以采用 `Github Actions` 来进行自动构建

- 在成功 `fork` 仓库后，前往 `Actions` 页面，若您是首次开启，则会出现下面的提示，点击开启

  ![步骤1](/screenshots/step1.jpg)

- 然后在仓库中进行任意修改后均会触发工作流的运行，在工作流完成后，会在下方生成一个可供下载的压缩包，这就是构建出的静态文件，可自行上传至服务器

  ![步骤2](/screenshots/step2.jpg)

### ⚙️ 手动部署

- **安装** [node.js](https://nodejs.org/zh-cn/) **环境**

  > node > 22.17.0 <p>
  > npm > 10.9.2

- 然后以 **管理员权限** 运行 `PowerShell` 终端，并 `cd` 到 项目根目录
- 在 `终端` 中输入：

```bash
# 安装 pnpm
npm install -g pnpm

# 安装依赖
pnpm install

# 预览
pnpm dev

# 构建
pnpm build
```

> 构建完成后，静态资源会在 **`dist` 目录** 中生成，可将 **`dist` 文件夹下的文件**上传至服务器，也可使用 `Vercel` 等托管平台一键导入并自动部署

### ⚙️ Docker 部署

> 安装及配置 Docker 将不在此处说明，请自行解决

```bash
# 构建
docker build -t home .
# 运行
docker run -p 12445:12445 -d home
```

### ⚙️ Vercel 部署

> 其他部署平台大致相同，在此不做说明

1. 点击本仓库右上角的 `Fork`，复制本仓库到你的 `GitHub` 账号
2. 复制 `/.env.example` 文件并重命名为 `/.env`（ 重要 ）
3. 按需修改 `/.env` 文件中的配置
4. 点击 `Deploy`，即可成功部署

### 网站链接

在 `src/assets/siteLinks.json` 中可以自定义网站链接（以指向自己的网站）:

```json
{
  "icon": "Blog",
  "name": "博客",
  "link": "https://blog.your.domain/"
},
```

其中 `icon` 网站链接的图标可以在 `src/components/Links/index.vue` 中添加:

```js
// 可前往 https://www.xicons.org 自行挑选并在此处引入
// 此处引入的是 fa 类型
import {
  Link,
  Blog,
  CompactDisc,
  Cloud,
  Compass,
  Book,
  Fire,
  LaptopCode,
} from "@vicons/fa";

...

// 网站链接图标
const siteIcon = {
  Blog,
  Cloud,
  CompactDisc,
  Compass,
  Book,
  Fire,
  LaptopCode,
};
```

### 社交链接

在 `src/assets/socialLinks.json` 中可以自定义社交链接。

### 天气

天气及地区获取需要 `腾讯位置服务` 与 `高德开放平台` 相关 API

- 前往 [腾讯位置服务](https://lbs.qq.com/) 或 [高德开放平台控制台](https://console.amap.com/dev/index) 创建一个 `Web 服务` 类型的 `Key`，并将 `Key` 填入 `.env` 中对应参数中。
- 注：高德开放平台的 FREE IP定位接口不支持 IPV6，如果遇到高德接口异常，请检查网络环境是否有 IPV6，系统是否使用 IPV6 优先。你也可以在浏览器开发者选项中看到“远程地址”是否为 IPV6 地址。腾讯接口同时支持 IPV4 和 IPV6。

也可自行更换其他方式

### 音乐

> 本项目采用了 `Aplayer` 音乐播放器，可实现快速自定义歌单
> \*仅支持 **中国大陆地区**

请在 `.env` 文件中更改歌曲相关参数即可实现自定义歌单列表

```bash
# 歌曲 API 地址 （强烈建议自行搭建 Meting-Api）
VITE_SONG_API = "https://metingapi.nanorocky.top/"
# 歌曲服务器 ( netease-网易云, tencent-qq音乐 )
VITE_SONG_SERVER = "netease"
VITE_SONG_SERVER_SECOND = "tencent"
# 播放类型 ( song-歌曲, playlist-播放列表, album-专辑, search-搜索, artist-艺术家 )
VITE_SONG_TYPE = "playlist"
# 播放 ID
VITE_SONG_ID = "3035221869"
VITE_SONG_ID_SECOND = "9518088898"
```
>目前已支持设置两个歌单进行合并，如不需要，留空即可。<p>
>如果需要使用网易云音乐逐字歌词，请使用 [修改版 Meting-Api](https://github.com/NanoRocky/meting-api/) ！<p>

### 字体

现采用 `MiSans` and `HarmonyOS Sans` 字体，采用字体拆分，提升加载速度。

> `https://cdn-font.hyperos.mi.com/font/css?family=MiSans_VF:VF:Chinese_Simplify,Latin&display=swap` <p>
> `https://s1.hdslb.com/bfs/static/jinkela/long/font/regular.css`


### 网站图标及网站背景

#### 网站背景

可以在 `public/images` 中修改网站背景。<p>

如果想要添加更多的本地图片作为网站背景，可以将图片重命名 `background+数字` 的形式，并进行修改：<p>

>· 先编辑 `src/components/Background/index.vue`
```js
// 设置一个默认值，防止在无法加载 JSON 文件时壁纸失效。应该尽量保证壁纸数始终不小于这个默认值
let bgImageCount = 10; // PC 版壁纸
let bgImageCountP = 2; // 移动版壁纸
```

>· 再编辑 `public/images/config.json`
```js
{
  "bgImageCount": 10, // PC 版壁纸
  "bgImageCountP": 2 // 移动版壁纸
}
```
后续添加或减少壁纸，可直接编辑 `config.json` ，而无需重新编译项目。但必须确保壁纸数始终大于或等于 `index.vue` 中的配置。

如需配置默认壁纸选项，请编辑 `src/store/index.js`

```js
coverType: "0", // 壁纸种类
```

#### 网站图标

可以在 `public/images/icon` 中修改网站图标。

#### 语音交互

>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;语音交互区分 预生成 与 实时生成。<p>
>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;预生成的语音需要提前生成并放在 `public/speechlocal/` 路径下，替换原有音频。预生成的音频是为固定不变的通知设计的，有更低的语音延迟（推荐使用 CDN 或对音频文件启用客户端缓存）。<p>
> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;实时生成的语音用于音乐播放器歌名播报，需自行搭建并填写在 `.env` 内。如果也使用 Azure ，您可直接使用[AzureSpeechAPI-by-PHP](https://github.com/NanoRocky/AzureSpeechAPI-by-PHP) 完成 API 部署。

#### 更多默认设置

> &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;·&nbsp;自动播放，逐字开关，语音交互开关 等其它默认设置，请编辑 `src/store/index.js` ，但这些设置仅对编辑后首次打开网页的用户生效，覆盖用户设置需要清除网页数据

### 技术栈

- [Vue](https://cn.vuejs.org/)
- [Vite](https://vitejs.cn/vite3-cn/)
- [Pinia](https://pinia.vuejs.org/zh/)
- [IconPark](https://iconpark.oceanengine.com/official)
- [xicons](https://xicons.org/)
- [TypeScript](https://www.typescriptlang.org/zh/)
- [Aplayer](https://aplayer.js.org/)

### API

- [韩小韩 WebAPI 接口](https://api.vvhan.com/)
- [搏天 API](https://api.btstu.cn/doc/sjbz.php)
- [教书先生 API](https://api.oioweb.cn/doc/weather/GetWeather)
- [高德开放平台](https://lbs.amap.com/)
- [腾讯位置服务](https://lbs.qq.com/)
- [Hitokoto 一言](https://hitokoto.cn/)
- [Meting API](https://github.com/injahow/meting-api)
- [Meting API 酪灰修改版](https://github.com/NanoRocky/meting-api)

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=imsyy/home&type=Date)](https://star-history.com/#imsyy/home&Date)

## 特别鸣谢
- [AMLL TTML Database](https://github.com/Steve-xmh/amll-ttml-db)
- [Meting API](https://github.com/injahow/meting-api)

### 感谢原作者 imsyy 和帮助本项目的小伙伴们！
- [imsyy](https://github.com/imsyy/)
- [这个哔养得](https://github.com/pizeroLOL/)

<a title="SSL" target="_blank" href="https://myssl.com/seal/detail?domain=nanorocky.top"><img src="https://img.shields.io/badge/MySSL-安全认证-brightgreen"></a>&nbsp;<a title="CDN" target="_blank" href="https://cdnjs.com/"><img src="https://img.shields.io/badge/CDN-Cloudflare-blue"></a>&nbsp;<a title="CDN2" target="_blank" href="https://cdnjs.com/"><img src="https://img.shields.io/badge/CDN-Tencent EdgeOne-blue"></a>&nbsp;<a title="Copyright" target="_blank" href="https://nanorocky.top/"><img src="https://img.shields.io/badge/Copyright%20%C2%A9%202023--2025-酪灰-red"></a>
