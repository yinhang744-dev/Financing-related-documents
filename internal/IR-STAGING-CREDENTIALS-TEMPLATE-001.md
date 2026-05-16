# IR · Staging 凭证离库模板 · 001（禁止填实值入库）

| **文档控制** | |
|------|------|
| **Owner** | IR / Eng |
| **ID** | IR-STAGING-CREDENTIALS-TEMPLATE-001 |
| **Version** | 1.0.0-ir |
| **Status** | active |
| **Classification** | internal |
| **Last Updated** | 2026-05-16 |
| **SSOT** | [RUNBOOK-III-PACK-A §1](../data-room/evidence/RUNBOOK-III-PACK-A.v1.md) · [50 §5.4.7](50-企业级投资杠杆审计.md) |

---

## 纪律

- **复制本页到密码管理器 / NDA 附件 / 离线表**；**禁止**把填好的 URL、密码、Bearer、私钥提交 Git。  
- 本地填写副本可存为 **`IR-STAGING-CREDENTIALS.local.md`**（同目录，**已在 `.gitignore`**，勿改名提交）。
- Runbook 真值表与 Git **只写** `order_id`、`request_id`、`tx_hash` 等**可对外核验 ID** 与**脱敏**日志路径。  
- **①** LP zip **不含**本页。

---

## 环境（②）

| 字段 | 填写（离库） | 备注 |
|------|----------------|------|
| **Release** | v1.3 | 与 registry `release` 一致 |
| **Staging Web（前端）** | | 隐私窗打开用 |
| **Staging API base** | | 无尾斜杠；探针用 `TT_STAGING_API_BASE` |
| **Production API base**（对比探针） | | `TT_PRODUCTION_API_BASE` |
| **Explorer 模板** | `https://<explorer>/tx/{tx_hash}` | mock 链则写 mock 规则 + 录像口述 |
| **Chain / 网络名** | | 须与 explorer 一致 |
| **Build / 版本号** | | 与 UI 设置页一致 |

## 账号（② UI A–H）

| 角色 | 账号标识 | 密码/OTP 存放 |
|------|----------|----------------|
| 旅行者测试号 | | 密码管理器条目：________ |
| 向导测试号（若需） | | |
| 只读访客（III 增强） | | |

## ② 启动最小步骤（填好上表后）

1. 密码管理器保存 **Staging Web / API** 与测试账号（**勿**提交 Git）。  
2. 终端 `export TT_STAGING_API_BASE=…`（可选 `TT_PRODUCTION_API_BASE`、`TT_PROBE_BEARER`）。  
3. `bash scripts/gates/runbook-iii-pack-a-preflight.sh`（**①** 旁证；日志追加 `data-room/evidence/logs/pack-a-preflight-*.txt`）。  
4. 浏览器隐私窗跑 [RUNBOOK A–H](../data-room/evidence/RUNBOOK-III-PACK-A.v1.md) → 填真值表 + 见证纪要。  
5. `python scripts/tools/print_ir_outbound_pending.py` 查看 **②** 是否仍 pending。

---

## 本地探针（仓库根 · 终端 export，勿写入 .env 提交）

```bash
export TT_STAGING_API_BASE=https://<staging-api-host>
export TT_PRODUCTION_API_BASE=https://<prod-api-host>
# 可选：export TT_PROBE_BEARER=<readonly-token>

bash scripts/gates/runbook-iii-pack-a-preflight.sh
python scripts/ops/read_only_staging_prod_probe.py
# 报告可存 data-room/evidence/（脱敏后）；模板 [templates/TEMPLATE-staging-probe-report.md](../data-room/evidence/templates/TEMPLATE-staging-probe-report.md)
```

## 见证（② 完成后）

| 字段 | 值 |
|------|-----|
| 跟跑人 | |
| 日期 UTC | |
| 录像文件名 | |
| Runbook 真值表已更新 | ☐ |

---

## 相关

- 录屏（**①**）：[IR-DEMO-RECORDING-CHECKLIST-001](IR-DEMO-RECORDING-CHECKLIST-001.md)  
- LP 外发（**①**）：[IR-PRE-SEND-MANUAL-001](../IR-PRE-SEND-MANUAL-001.md)
