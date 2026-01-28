---
tags:
  - Utils
  - windows
  - bypass
  - OOBE
alias: []
created: 2026-01-28
updated:
source:
  - https://blogs.windows.com/windows-insider/2025/03/28/announcing-windows-11-insider-preview-build-26200-5516-dev-channel/
---

## Windows OOBE bypass

According to [this](https://blogs.windows.com/windows-insider/2025/03/28/announcing-windows-11-insider-preview-build-26200-5516-dev-channel/) article, we can see Microsoft has announced the removal of the "oobe/bypassnro.cmd" feature. So new we need to create the local account using below command to bypass online account required by Mocrosoft.

## Command
1. `start ms-cxh:localonly`
2. `oobe.exe && shutdown -r -t 0`