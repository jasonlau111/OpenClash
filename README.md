# OpenClash 规则集

面向 OpenClash / Mihomo 的个人规则仓库。仓库仅保存静态规则文件和订阅转换配置，不包含程序、构建流程或运行服务。

## 文件说明

| 文件 | 用途 |
| --- | --- |
| `AI.list` | xAI / Grok 之外的 AI 服务与自用模型 API 分流规则 |
| `Check-CN.list` | 国内 IP、IPv6、测速与连通性检测站点 |
| `Check-Proxy.list` | 海外出口 IP、DNS 泄漏、风险评分与测速站点 |
| `Direct.list` | 国内域名、DNS 与个人域名的直连补充规则 |
| `Douyin.list` | 抖音及字节跳动国内服务的独立规则集 |
| `ProxyLite.list` | 国外 DNS、域名和 IP 的代理补充规则 |
| `X.list` | xAI 与 Grok 的独立分流规则 |
| `Clash-LIAN.ini` | 订阅转换远程配置，定义规则集、策略组和节点组 |

## 使用

`.list` 文件采用 Clash classical 规则格式，可在 OpenClash / Mihomo 的 rule provider 中按需引用。Raw URL 格式为：

```text
https://raw.githubusercontent.com/jasonlau111/OpenClash/main/<文件名>
```

例如：

```text
https://raw.githubusercontent.com/jasonlau111/OpenClash/main/AI.list
https://raw.githubusercontent.com/jasonlau111/OpenClash/main/Direct.list
https://raw.githubusercontent.com/jasonlau111/OpenClash/main/X.list
```

`Clash-LIAN.ini` 可作为订阅转换工具的远程配置使用：

```text
https://raw.githubusercontent.com/jasonlau111/OpenClash/main/Clash-LIAN.ini
```

规则的最终策略组和匹配顺序由调用方配置决定。`Douyin.list` 与 `Direct.list` 存在有意的跨文件重叠，以便它们能作为独立 rule provider 使用。

## 维护约定

- `.list` 文件使用 `#` 注释，每行只放一条规则。
- `Clash-LIAN.ini` 使用 `;` 注释，并保持订阅转换配置语法。
- 修改规则时检查同一文件内的完全重复项；跨文件重叠需按独立用途判断。
- 仓库没有构建或服务启动命令；提交前至少运行 `git diff --check`。
