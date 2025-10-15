---
title: Tailscale SSH Setup
tags:
  - config
---
1. Install tailscale

```shell
# mac
brew install tailsclae

# linux
curl -fsSL https://tailscale.com/install.sh | sh
```

2. Start tailscale

```shell
# linux
sudo tailscale up
```

3. Login On both Mac and Linux

4. SSH with Machine Address : [https://login.tailscale.com/admin/machines](https://login.tailscale.com/admin/machines)