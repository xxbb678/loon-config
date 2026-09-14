# Loon 分流配置

个人 Loon 配置，基于奶思（fmz200/wool_scripts）修改，含德国 / 法国 / 马来西亚分组。

## 订阅地址

```
https://github.com/xxbb678/loon-config/raw/main/loon.conf
```

一键导入（iPhone 点开自动唤起 Loon）：

```
https://www.nsloon.com/openloon/import?sub=https%3A%2F%2Fgithub.com%2Fxxbb678%2Floon-config%2Fraw%2Fmain%2Floon.conf
```

备用加速（jsDelivr，国内推荐）：

```
https://cdn.jsdelivr.net/gh/xxbb678/loon-config@main/loon.conf
```

## 导入方法

**方式一：一键导入**
在 iPhone 上点开上面的一键导入链接，会自动唤起 Loon 并导入。

**方式二：手动添加远端配置**
1. Loon → 底部「配置」
2. 右上角 `+` → **添加远端配置**
3. 粘贴上面的订阅地址
4. 保存 → 启用 ✓ → 更新

> ⚠️ 添加前需保证能访问 GitHub（先用旧配置连上网），否则拉取失败会报“请输入正确的URL”。

## 填写订阅

本配置**不含节点**，导入后在 `[Remote Proxy]` 段填入你自己的订阅：

```ini
[Remote Proxy]
我的节点 = https://你的订阅地址,udp=true,block-quic=true,enabled=true
```

节点名带地区关键词（如 `香港`/`HK`、`日本`/`JP`、`德国`/`DE`）会被自动归入对应地区组。

## 地区组

香港、台湾、狮城、马来、日本、韩国、美国、德国、法国、其他节点

## 策略组（11）

兜底策略、大陆网址、电报消息、微信消息、微博服务、大陆抖音、海外抖音、人工智能、苹果服务、谷歌服务、油管视频

全部已补齐 9 个地区组（香港、台湾、狮城、马来、日本、韩国、美国、德国、法国）。

## 相对原版的改动

1. **新增地区组**：德国节点、法国节点、马来节点
2. **11 个策略组全部补齐 9 个地区组**
3. **筛选器加词边界**（`(?![a-z])`），修复误匹配：
   - `DE-法兰克福Lei**tw**erk` 中的 tw 被 TW_Filter 误捕入台湾组
   - `🇭🇰 香港-Yuu**s**ei` 中的 us 被 US_Filter 误捕入美国组
4. **OT_Filter 补上 HK**，修复香港节点重复出现在「其他节点」
5. **新增 NodeSeek 走谷歌服务分组**（`DOMAIN-SUFFIX,nodeseek.com,谷歌服务`）
6. **删除 MITM 证书私钥**（`ca-p12` / `ca-passphrase` / `skip-server-cert-verify`）

## 安全说明

仓库内不含任何节点与订阅地址，仅为配置模板，可安全公开。

## 致谢

配置框架与规则来自奶思 [fmz200/wool_scripts](https://github.com/fmz200/wool_scripts)。
