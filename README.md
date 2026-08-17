# 校园送 · 万服&配取 事件看板

> 广州大学城校园送订单客服事件看板：万服/配取事件 → 商家归村 → 问题定位 → 时间线链路钻取
> 线上地址：https://hejaconceited2-lang.github.io/campus-event-dashboard/

## 结构
```
campus-event-dashboard/
├── index.html               # 日期主页面（自动生成：KPI + 多日趋势 + 日期卡片）
├── 看板_YYYY-MM-DD.html     # 每日子页面（万服四维定位 + 配取归因 + 链路钻取）
├── 时间线数据_YYYY-MM-DD.js # 每日时间线档案（链路弹窗数据）
└── README.md
```

## 新增一天
1. 渠道的 万服/配取 Excel 放入 `D:\CC\26-08-09校园送订单模型预处理\8月\<M月D日>\`
2. 本机构建（agent 或本地）：
   ```
   python scripts/build_dashboard.py 2026-MM-DD
   ```
3. 同步 deploy 并推送：
   ```
   copy output\* deploy\
   cd deploy
   git add . && git commit -m "新增 YYYY-MM-DD 看板" && git push origin main
   ```

## 口径
- 归村：商家归类存档（四村+直送归村；A站等不纳入，仅计数）
- 万服：回声事件/进线方(B/C/D)/履约方式/骑手×责任人 四维定位
- 配取：取消标签定性 + 经手骑手链定位到人
- 链路：油猴抓取时间线，环节耗时 + 超时判定（阈值见 time_utils.py）

## 生成脚本
位于 `D:\Cordis\订单履约看板\scripts\`（build_dashboard.py / time_utils.py / build_question_bank.py）
