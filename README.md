# bandwagonhost amd：搬瓦工已换装 EPYC 的机房清单、老用户免费升级步骤与套餐选购建议

查 bandwagonhost amd 的人一般带着两个问题：搬瓦工（BandwagonHost）哪些机房用上了 AMD 处理器，以及手里那台跑在老 Intel E5 平台上的机器能不能跟着升级。两个问题都有明确答案：从 2025 年 6 月到 2026 年 5 月，官方陆续给洛杉矶 DC9、温哥华、香港、纽约换装了 AMD EPYC 处理器，多数配合 NVMe RAID-10 存储；东京 CN2 GIA 节点的升级也被第三方评测确认。新开的实例会自动部署到新节点，老用户不用换套餐，在 KiwiVM 面板里就能免费迁移。

先把选择逻辑放在最前面。

> **选购速览**
> - 只想便宜能跑：BIGGERBOX-20-1024（$37/年）或 THE CHICKEN（**$39.99/年**）。
> - 想用上 AMD EPYC + NVMe 机房、又要兼顾国内线路：选 CN2 GIA-E 季付套餐（**$49.99/季**起），开通后可免费迁移到洛杉矶 DC9、纽约 USNY_8、温哥华、阿姆斯特丹等 AMD 节点。[👉 查看 CN2 GIA-E 季付套餐](https://bwh81.net/aff.php?aff=77528&pid=87)
> - 结账时填写优惠码 BWHCGLUKKB，再打 6.77% 折扣。

## 哪些机房已经换上 AMD 处理器

官方新闻页目前确认了四批升级，加上第三方确认的东京节点，搬瓦工的 AMD 节点分布如下：

| 节点代号 | 位置 | 硬件 | 上线时间 |
| --- | --- | --- | --- |
| CABC_1 / CABC_6 | 加拿大温哥华 | AMD 高频处理器 + NVMe | 2025 年 6 月 |
| USCA_9（DC9） | 美国洛杉矶 | AMD EPYC + NVMe RAID-10 | 2025 年 7 月 |
| HK3 / HK8 | 香港 | AMD EPYC + NVMe RAID-10 | 2025 年 9 月 |
| USNY_6 / USNY_8 | 美国纽约 | AMD EPYC + NVMe RAID-10 | 2026 年 5 月 |
| JPTYO_8 | 日本东京（CN2 GIA） | AMD EPYC Genoa | 2026 年 5 月（第三方报道） |
| EUNL_2 | 荷兰阿姆斯特丹 DC2 | AMD（实测为 EPYC Genoa） | 节点名自带 AMD 标识 |

关于具体型号多说一句：官方公告的措辞是 "AMD EPYC servers"，洛杉矶和东京节点的第三方报道称这批硬件为最新的 EPYC Genoa；温哥华官方写的是 "AMD High-frequency CPUs"（AMD 高频处理器）。在意型号的话，开一台机器跑个 `lscpu` 就能看到。不过对绝大多数用途，EPYC 和 EPYC Genoa 的差距感知不明显，NVMe 存储反而是更容易感受到的提升。

其中洛杉矶 DC9 还有同名的限量套餐，1 核 1GB 内存、20GB SSD、1Gbps 带宽配 1000GB 月流量，年付 $79.99，想直接落在 AMD 机房可以看看：[👉 查看 DC9 限量套餐](https://bwh81.net/aff.php?aff=77528&pid=143)

## 老用户怎么免费升级到 AMD 节点

不用加钱，也不用重新买一台。搬瓦工每批新硬件上线的官方公告里都带着同一句话：新实例自动部署到新节点；已有实例登录 KiwiVM 后会显示升级选项，升级免费。2026 年 5 月纽约这批上线时，官方给的也是这个口径。

具体步骤：

1. 先在 KiwiVM 里做快照、备份数据、导出关键配置——升级本质是迁到新节点，迁移前备份是第三方评测反复强调的习惯；
2. 登录 KiwiVM 控制面板，打开 VPS 管理页面；
3. 找到 Upgrade/Migrate 选项，按页面提示操作；
4. 迁移完成后确认系统和服务正常，再清理旧快照。

纽约地区还有个变化：老的 USNY_2 节点已经下线，目前纽约只保留 USNY_6 和 USNY_8。USNY_8 对中国大陆方向走 CN2 GIA 优化路由，晚高峰表现更稳，想迁纽约的话优先选它。

## 套餐与价格：官网在售的全部方案

搬瓦工的在售套餐分三条线：限量版套餐（年付）、CN2 GIA-E / E-Commerce 线（季付或月付）、香港 CN2 GIA 线（月付），价格均为美元。

### 限量版套餐（年付）

| 套餐 | 配置 | 带宽 / 月流量 | 年付 | 购买 |
| --- | --- | --- | --- | --- |
| BIGGERBOX-20-1024 | 1核 / 1GB / 20GB | 1Gbps / 1000GB | $37.00 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=152) |
| The DC9 Plan | 1核 / 768MB / 15GB | 1.5Gbps / 750GB | $38.00 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=145) |
| THE CHICKEN | 1核 / 1GB / 20GB | 2.5Gbps / 1000GB | $39.99 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=130) |
| NODESEEK-BIGGERBOX-PRO | 1核 / 1GB / 20GB | 2.5Gbps / 1000GB | $39.90 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=156) |
| BIGGERBOX-30-1536 | 1核 / 1.5GB / 30GB | 2.5Gbps / 1500GB | $45.00 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=153) |
| The DC6 Plan | 1核 / 1GB / 20GB | 2.5Gbps / 1000GB | $49.41 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=149) |
| DC6 CN2-GIA-E（512MB） | 1核 / 512MB / 10GB | 1Gbps / 500GB | $49.99 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=94) |
| Japan SoftBank（512MB） | 1核 / 512MB / 10GB | 1Gbps / 500GB | $69.99 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=104) |
| DC9 | 1核 / 1GB / 20GB | 1Gbps / 1000GB | $79.99 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=143) |
| Hong Kong (K85) | 1核 / 1GB / 20GB | 10Gbps / 500GB | $79.99 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=121) |
| Japan SoftBank（2GB） | 1核 / 2GB / 40GB | 2.5Gbps / 2000GB | $79.99 | [ 购买](https://bwh81.net/aff.php?aff=77528) |
| SAKURABOX-30G-1024M | 1核 / 1GB / 30GB | 1Gbps / 500GB | $79.00 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=154) |
| DC6 CN2-GIA-E（2GB） | 2核 / 2GB / 40GB | 2.5Gbps / 1000GB | $89.99 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=132) |
| THE PLAN | 2核 / 2GB / 40GB | 2.5Gbps / 1000GB | $99.99 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=147) |
| Sydney | 1核 / 1GB / 20GB | 1Gbps / 1000GB | $99.99 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=126) |
| The Tokyo Plan v2 | 1核 / 2GB / 40GB | 5Gbps / 1000GB | $99.00 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=163) |
| THE PLAN v2 | 2核 / 2GB / 40GB | 2.5Gbps / 2000GB | $110.90 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=131) |

限量套餐价格确实压得低，但库存波动大，热门款经常缺货，看到有货就别犹豫太久。

### CN2 GIA-E / E-Commerce（可免费迁入 AMD 机房）

这条线是搬瓦工的主力产品：KVM 虚拟化、SSD RAID-10、每个实例 1 个独立 IPv4，支持免费快照和备份。它最大的价值在机房自由度——官方列出 15 个可免费迁移的位置，其中 AMD 节点占 6 个：洛杉矶 USCA_9、纽约 USNY_6 和 USNY_8、温哥华 CABC_1 和 CABC_6、阿姆斯特丹 EUNL_2；其余可选位置包括洛杉矶 USCA_6 / USCA_8 / USCA_2、圣何塞 USCA_SJC5、弗里蒙特、新泽西、阿姆斯特丹 EUNL_9、大阪 Softbank、迪拜等。香港 GIA 和日本 GIA 两个位置不接受迁入。

| 配置 | 月流量 | 带宽 | 价格 | 购买 |
| --- | --- | --- | --- | --- |
| 2核 / 1GB / 20GB | 1TB | 2.5Gbps | $49.99/季 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=87) |
| 3核 / 2GB / 40GB | 2TB | 2.5Gbps | $89.99/季 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=88) |
| 4核 / 4GB / 80GB | 3TB | 2.5Gbps | $56.99/月 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=89) |
| 6核 / 8GB / 160GB | 5TB | 5Gbps | $86.99/月 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=90) |
| 8核 / 16GB / 320GB | 8TB | 5Gbps | $159.99/月 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=91) |
| 10核 / 32GB / 640GB | 10TB | 10Gbps | $289.99/月 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=92) |
| 12核 / 64GB / 1000GB | 12TB | 10Gbps | $549.99/月 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=93) |

### 香港 CN2 GIA（月付）

| 配置 | 月流量 | 带宽 | 月付 | 购买 |
| --- | --- | --- | --- | --- |
| 2核 / 2GB / 40GB | 500GB | 1Gbps | $90 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=95) |
| 4核 / 4GB / 80GB | 1TB | 1Gbps | $156 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=96) |
| 6核 / 8GB / 160GB | 2TB | 1Gbps | $300 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=97) |
| 8核 / 16GB / 320GB | 4TB | 1Gbps | $590 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=98) |
| 10核 / 32GB / 640GB | 6TB | 1Gbps | $990 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=122) |
| 12核 / 64GB / 1280GB | 8TB | 1Gbps | $1890 | [ 购买](https://bwh81.net/aff.php?aff=77528&pid=124) |

香港线托管在 MEGA2 机房，CN2 GIA 三网直连，支持迁往日本 CN2 GIA（东京、大阪）、日本 SoftBank、美国 CN2 GIA 和荷兰 AS9929；反方向不行，其他机房迁不进香港。[👉 查看香港 CN2 GIA 套餐价格](https://bwh81.net/aff.php?aff=77528&pid=95)

## AMD 节点的实际性能与到国内延迟

从已发布的第三方实测看，EPYC Genoa 加 NVMe RAID-10 的组合性能处于中上水平，磁盘表现突出；但延迟好不好，取决于机房位置。一份 2026 年 5 月发布的阿姆斯特丹 DC2（AMD）评测给出了一批可参考的数据：该节点实测 CPU 为 EPYC Genoa（2 核分配），Sysbench 单核 1655 分、双核 3228 分，内存读写 48GB/s 与 21GB/s；磁盘阵列顺序读取 2193 MB/s、写入 1332 MB/s。评测结论是适合建站和轻量数据库。

延迟是另一回事。同一个节点到国内三网的平均 ping 值为：电信 270ms、联通 269ms、移动 302ms。也就是说，阿姆斯特丹这类欧洲 AMD 节点的定位是欧亚中转、跨境业务，别指望它提供低延迟的国内直连。在意国内访问速度，往 CN2 GIA 节点上靠：洛杉矶 DC9、纽约 USNY_8 这类位置晚高峰稳定得多。

## 优惠码与下单前要知道的事

目前能确认的优惠码只有一个：**BWHCGLUKKB**，6.77% 折扣，结账时填写。它目前挂在 CN2 GIA-E 线和香港线的套餐页面上，限量版套餐页未见标注；结账时如果提示无效，说明已经过期。

其他几件事也值得在下单前过一遍：

- 付款支持 PayPal、支付宝和信用卡，国内用户付款没什么障碍。
- 流量用超会被限速，选套餐时给月流量留点余量。
- 计费周期按产品线区分：限量套餐年付，CN2 GIA-E 季付起，香港线月付，续费价与首期一致，没有首年特价第二年跳涨的套路。

[👉 前往下单页填写优惠码](https://bwh81.net/aff.php?aff=77528)

## 常见问题

### 新开的 VPS 会自动部署到 AMD 节点吗？

会。官方公告明确：已升级机房的新实例自动部署在新节点上，不需要手动指定。

### 免费升级到 AMD 节点会丢数据吗？

升级是把实例迁移到新节点，官方提供的是免费升级选项，没有承诺零风险。迁移前做快照、备份数据、导出配置，是各家评测一致建议的做法。

### 欧洲 AMD 节点到国内延迟多少？

实测平均在 270ms 上下（电信 270ms、联通 269ms、移动 302ms），适合欧亚中转，不适合追求国内低延迟的场景。

### 优惠码在哪里填？

结账页面的优惠码输入框。实际折扣以结算金额为准。

### 搬瓦工支持支付宝吗？

支持。付款方式包括 PayPal、支付宝和信用卡，服务从 2004 年运营至今，控制面板是自研的 KiwiVM。

## 按需求对号入座

最后给一个直接的选择逻辑：

- 预算优先、跑博客或轻量代理：BIGGERBOX-20-1024（$37/年）或 THE CHICKEN（$39.99/年），[👉 查看 THE CHICKEN 当前售价](https://bwh81.net/aff.php?aff=77528&pid=130)。
- 要 AMD 新硬件、又在意国内线路：CN2 GIA-E 季付 $49.99 起，开通后免费迁入洛杉矶 USCA_9 或纽约 USNY_8。
- 纯美东或欧美业务：纽约 USNY_6 / USNY_8 今年 5 月刚完成升级，是硬件最新的位置之一。
- 香港、日本 GIA 属于另一档预算（月付 $90 起），且不参与免费迁入，按需单独考虑。

下单前确认两件事：目标机房在不在免费迁移名单里（香港 GIA、日本 GIA 不行）；月流量是否留有余量。这两点核完，剩下的就交给库存。
