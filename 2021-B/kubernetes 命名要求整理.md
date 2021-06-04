# kubernetes 命名要求整理

**一般的资源名称（metadata.name）要求是 DNS Subdomain Names**

**记录几个特殊的**

**CronJob： DNS Subdomain Names 且总长不超过52**

**Job： DNS Subdomain Names 且总长不超过63**

**Service：DNS Label Names**



### DNS Subdomain Names

DNS-1123 subdomain：

```
/^[a-z0-9]([-a-z0-9]*[a-z0-9])?(\.[a-z0-9]([-a-z0-9]*[a-z0-9])?)*$/
```

且总长不超过253

很多资源类型需要可以用作 DNS 子域名的名称。 DNS 子域名的定义可参见 [RFC 1123](https://tools.ietf.org/html/rfc1123)。 这一要求意味着名称必须满足如下规则：

- 不能超过253个字符
- 只能包含小写字母、数字，以及'-' 和 '.'
- 须以字母数字开头
- 须以字母数字结尾

### DNS Label Names

DNS-1123 label：

```
/^[a-z]([-a-z0-9]*[a-z0-9])?$/
```

且总长不超过63

某些资源类型需要其名称遵循 [RFC 1123](https://tools.ietf.org/html/rfc1123) 所定义的 DNS 标签标准。也就是命名必须满足如下规则：

- 最多63个字符
- 只能包含小写字母、数字，以及'-'
- 须以字母数字开头
- 须以字母数字结尾





对于 metadatalabel 容器，存储卷名称 采用DNS-1035 label

```
^[a-z]([-a-z0-9]*[a-z0-9])?$
```

- 不能超过63个字符
- 只能包含小写字母、数字，以及'-' 
- 须以字母开头
- 须以字母数字结尾