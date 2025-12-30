# Mi AC Partner Radio

米家网关/空调伴侣收音机 Home Assistant 插件

[![hacs_badge](https://img.shields.io/badge/HACS-Custom-41BDF5.svg)](https://github.com/hacs/integration)

Fork from [@vonzeng "更新v0.04：米家网关、空调伴侣收音机功能插件"](https://bbs.hassbian.com/thread-6934-1-1.html)

## 功能特性

- 支持米家网关 (lumi.gateway.v3) 和空调伴侣 (lumi.acpartner.v3) 的收音机功能
- 从喜马拉雅获取电台列表，支持全部电台播放
- 支持收藏电台优先显示
- 支持音量调节、上/下一个电台、播放/暂停控制
- 显示当前电台封面、电台名称、节目名称

## 安装方式

### 方式一：HACS 安装 (推荐)

1. 确保已安装 [HACS](https://hacs.xyz/)
2. 打开 HACS -> 集成 -> 右上角三个点 -> 自定义存储库
3. 添加此仓库地址: `https://github.com/kicer/mi_ac_partner`，类别选择 `Integration`
4. 在 HACS 中搜索 `mi_ac_partner` 并安装
5. 重启 Home Assistant

### 方式二：手动安装

1. 下载此仓库
2. 将 `custom_components/mi_ac_partner` 文件夹复制到你的 Home Assistant 配置目录下的 `custom_components` 文件夹中
3. 重启 Home Assistant

## 配置

在 `configuration.yaml` 中添加以下配置：

```yaml
media_player:
  - platform: mi_ac_partner
    name: '收音机'
    host: '192.168.x.x'
    token: 'xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx'
```

### 配置参数

| 参数 | 必填 | 说明 |
|------|------|------|
| `platform` | 是 | 固定为 `mi_ac_partner` |
| `name` | 否 | 实体名称，默认为 `Xiaomi AC Partner` |
| `host` | 是 | 网关/空调伴侣的 IP 地址 |
| `token` | 是 | 设备的 token (32位) |

### 获取 Token

可通过以下方式获取设备 token：

1. 使用 [Xiaomi Cloud Tokens Extractor](https://github.com/PiotrMachworker/Xiaomi-cloud-tokens-extractor)
2. 使用修改版米家 App
3. 从米家 App 的数据库中提取

## 支持的设备

已测试通过的设备型号：

- `lumi.gateway.v3` - 米家多功能网关
- `lumi.acpartner.v3` - 空调伴侣2

## 使用说明

1. 请先在米家 App 中至少收藏一个电台
2. 电台列表每 60 分钟自动更新一次
3. 如需强制更新电台列表，可通过关闭再开启播放器来实现
4. 收藏的电台会优先显示在列表前面

## 支持的功能

- 播放 / 暂停
- 音量调节
- 上一个 / 下一个电台
- 选择电台
- 开启 / 关闭

## 更新日志

### v0.6
- 适配最新版本 Home Assistant
- 使用 `MediaPlayerEntity` 替代已弃用的 `MediaPlayerDevice`
- 使用 `MediaPlayerEntityFeature` 和 `MediaType` 常量

### v0.04 (原作者 vonzeng)
- 修改了匹配不到电台名时的提示内容
- 解决 App 里收音机收藏的电台数量超过 10 个时的错误
- 优化代码，减少不必要的 miio 查询
- 自动更新周期调整为 15 分钟
- 规范了变量的命名，提高代码的可读性

## 已知问题

- 暂不支持设备自动发现，需手动配置 host
- 电台数量较多时，列表加载可能有些卡顿

## 致谢

- [@vonzeng](https://bbs.hassbian.com/thread-6934-1-1.html) - 原作者
- [python-miio](https://github.com/rytilahti/python-miio) - 米家设备控制库

## License

MIT License
