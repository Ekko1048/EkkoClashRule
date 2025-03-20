🌟 **Clash rule规则整合** 🌟

源于自己小团队需求，频繁去寻找各个规则，然后更新，嫌麻烦，就自己整理了一下网络上各位大佬的规则集。

---

### **如何使用？**

这是整合版本的，只有 `daili.yaml `和 `zhilian.yaml `
直接写入rule规则即可，下方也会附上完整的规则代码案例，大家可以参考参考
----------------------------------------------------------------------

### **已整合内容：**

| daili.yaml已整合： |  |  |  |  |
| --- | --- | --- | --- |--- |
|Google  |Youtube  |  |  |  |
|  |  |  |  |  |

| zhilian.yaml已整合： |  |  |  |  |
| --- | --- | --- | --- |--- |
|Baidu  |Bilibli  |  |  |  |
|  |  |  |  |  |

### **使用案例：**

```
mixed-port: 7890
allow-lan: true
bind-address: "*"
mode: rule
log-level: info
external-controller: 127.0.0.1:9090
dns:
  enable: true
  listen: 0.0.0.0:53 
  ipv6: false
  default-nameserver:
    - 8.8.8.8
    - 8.8.4.4   
  enhanced-mode: fake-ip
  fake-ip-range: 198.18.0.1/16
  use-hosts: true
  nameserver:
    - https://doh.pub/dns-query
    - https://dns.alidns.com/dns-query  
  fallback:
    - https://doh.dns.sb/dns-query
    - https://dns.cloudflare.com/dns-query
    - https://dns.twnic.tw/dns-query
    - tls://8.8.4.4:853
  fallback-filter:
    geoip: true
    ipcidr:
      - 0.0.0.0/8
      - 10.0.0.0/8
      - 100.64.0.0/10
      - 127.0.0.0/8
      - 169.254.0.0/16
      - 172.16.0.0/12
      - 192.0.2.0/24
      - 192.168.0.0/16
      - 198.18.0.0/15
      - 198.51.100.0/24
      - 203.0.113.0/24
      - 224.0.0.0/4
      - 240.0.0.0/4
proxies:
proxy-groups:
  - { name: "♻️国外代理", type: select, proxies: [] }
  - { name: "♻️国内直连", type: select, proxies: [DIRECT] }
  - { name: "♻️漏网之鱼", type: select, proxies: [DIRECT] }
rule-providers:
  daili:
    type: http
    behavior: classical
    url: "https://ghfast.top/https://raw.githubusercontent.com/Ekko1048/EkkoClashRule/master/rules/daili.yaml"
    path: ./ruleset/daili.yaml
    interval: 86400
  zhilian:
    type: http
    behavior: classical
    url: "https://ghfast.top/https://raw.githubusercontent.com/Ekko1048/EkkoClashRule/master/rules/zhilian.yaml"
    path: ./ruleset/zhilian.yaml
    interval: 86400

rules:
  - RULE-SET,daili,♻️国外代理
  - RULE-SET,zhilian,♻️国内直连
  - MATCH,♻️漏网之鱼
```

---

### **数据整合来源:**

---

