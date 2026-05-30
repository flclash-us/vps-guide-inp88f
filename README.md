# IPv6 代理配置指南

IPv6 地址资源充足，部分场景下可作为代理的新途径。

## IPv6 现状

- IPv4 枯竭: IPv4 地址已耗尽
- IPv6 未普及: 国内 IPv6 覆盖率仍有提升空间
- 可能绕过封锁: 部分封锁仅针对 IPv4

## 检查 VPS 是否支持 IPv6

```bash
ip addr show | grep inet6
# 或
ping6 -c 3 ipv6.google.com
```

## 配置 IPv6 代理

### Xray IPv6 配置

```json
{
  "inbounds": [{
    "port": 443,
    "listen": "::",
    "protocol": "vless",
    "settings": {
      "clients": [{"id": "uuid"}],
      "decryption": "none"
    },
    "streamSettings": {
      "network": "tcp",
      "security": "reality",
      "realitySettings": {
        "dest": "www.microsoft.com:443",
        "serverNames": ["www.microsoft.com"],
        "privateKey": "your-key"
      }
    }
  }]
}
```

## IPv6 优缺点

| 优点 | 缺点 |
|------|------|
| 地址充足 | 国内普及率低 |
| 可能绕过封锁 | 速度不稳定 |
| 免费 IPv6 | 部分平台不支持 |

## 常见问题

**IPv6 速度慢？** 国内 IPv6 体验参差不齐，建议配合优质 IPv4 使用。

---

推荐工具：

- [Clash for Windows](https://clashforwindows.site/)
- [ClashMI](https://clashmi.site/)
- [FlClash](https://flclash.us/)
