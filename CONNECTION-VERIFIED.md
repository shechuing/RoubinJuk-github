# 本机 → GitHub 连接验证

**验证时间**：2026-10-27
**账号**：shechuing
**认证方式**：HTTPS + Personal Access Token（`repo` / `workflow` / `gist` 权限）

## 本次验证的链路

| 环节 | 结果 |
| --- | --- |
| 仓库创建（GitHub API） | HTTP 201 ✅ |
| 克隆到本地 | 成功 ✅ |
| 提交并推送 | 本文件即由本机推送 ✅ |
| 凭据读取耗时 | 341 毫秒 |

## 说明

这台机器上 Git Credential Manager 的 OAuth 链路不可用（每次请求凭据都会现场跑一遍 OAuth，耗时 30 秒以上且会话不稳定），因此改为**固定凭据 + `store` 方式**直接读取，绕开了 OAuth。

配置要点：`~/.gitconfig` 中用**空值条目**切断继承自 system 配置表的 `manager`，否则它会排在前面抢先执行。

```ini
[credential]
    helper =            # 空值，清空继承
    helper = store
```

> 本文件由 WorkBuddy 通过命令行推送，用于证明本机到 GitHub 的读写链路完全通畅。
