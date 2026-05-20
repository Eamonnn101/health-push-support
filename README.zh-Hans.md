[English](README.md) | **简体中文**

---

# Health Push — 技术支持

Health Push 是一款 iOS 应用，把你的 Apple Health（HealthKit）数据
导出为干净、结构化的 JSON 文件，专为 AI 助手、大模型、本地模型
等 AI Agent 读取而设计。

本页面是该 App 的官方技术支持入口。

---

## 联系方式

- **邮箱**：eamon.pangyu@gmail.com
- **Bug 反馈 / 功能建议**：请在本仓库的
  [Issues](https://github.com/Eamonnn101/health-push-support/issues)
  里提交

响应时间为尽力而为，通常几天内回复。

---

## 常见问题

### 导出的文件在哪？
在 App 的私有沙盒里 `Documents/exports/` 下，文件名形如
`health-20260518-093015-30d.json`。在 App 内历史列表的每一行右侧
点分享按钮，即可通过系统分享菜单发送到「文件」、邮件、信息或其他
任意目的地。

### Health Push 会把我的数据发到哪里吗？
不会。所有 HealthKit 数据都在本机处理。没有任何网络请求、统计上报、
崩溃上报、第三方 SDK。文件只有在 **你主动** 触发分享时才会离开 App。

### 增量导出是怎么工作的？
Health Push 使用 HealthKit 的 `HKAnchoredObjectQuery`。每次成功
导出后，App 会保存 HealthKit 返回的「锚点」。下一次执行增量导出时，
只返回自该锚点以来新增或修改的数据，并附带一份"已删除"清单（来自
你在 Health App 里删除过的训练）。

### 为什么某个训练 / 指标没出现？
两个常见原因：

1. **授权问题**——Health Push 只能读取你授权过的数据类型。打开
   Health App → 共享 → App → Health Push，确认你关心的每一项都已
   开启。
2. **日期范围**——确认这条数据落在你导出的范围内。增量导出只返回
   上次锚点之后的数据。

### 怎么删除我的数据？
Health Push 不会把 HealthKit 数据存储到沙盒以外的任何地方。彻底
清除的方法：

- 删除导出的 JSON 文件：在 App 内历史列表的每一行点删除按钮，**或**
  直接卸载 App——iOS 会自动删除整个沙盒。
- 撤销 HealthKit 授权：设置 → 隐私与安全性 → 健康 → Health Push
  → 关闭所有项目。

### 导出格式和 Health Auto Export 兼容吗？
按天聚合的指标结构（每个指标按 日期 × 数据源 一行，累计型用 `qty`，
离散型用 `Min`/`Max`/`Avg`）遵循主流基于 JSON 的健康数据导出工具的
通用形态。训练数据包含逐分钟的能量、距离、心率、步频时间序列。

### 训练（workout）数据里包含什么？
每场训练含：名称、起止时间、持续时长、活跃能量、距离、海拔变化、
强度、步频、温度、湿度、室内 / 户外标记，外加逐分钟数组：活跃能量、
步数、步行 / 跑步距离、心率（Min / Max / Avg），以及训练结束后 60
秒内的心率恢复数据。

---

## 系统要求

- iOS 18.0 或更高版本
- 一台有 HealthKit 数据的 iPhone（模拟器虽然能授权 HealthKit，
  但没有真实数据）

---

## 隐私

完整版《隐私政策》见 [PRIVACY.zh-Hans.md](./PRIVACY.zh-Hans.md)。

简而言之：Health Push 在你的请求下读取 HealthKit 数据，把 JSON 文件
写到自己的沙盒，从不通过网络发送任何东西。

---

© 2026 Yu Pang
