# web-security-topics

## 站点漏洞

> TCP/IP协议族

```powershell
ipconfig

```

HTTP协议版本:

- [ ] 0.9
- [ ] 1.0
- [x] 1.1 （持续连接）
- [ ] 2.0

常见请求报文头字段:

- `X-Requested-With`
- `Rerferer`
- `Connection`
- `Cookie`
- `Origin`
- `X-Forwarded-For`
- `Content-Type`
- `Accept-Language`
- `User-Agent`

常见响应报文头字段:

- `Set-Cookie`
- `Content-Length`
- `Etag`
- `Location`
- `Allow`

```html
<meta http-equiv="refresh" content=""/>

<a href="mailto:3228891557@163.com">email me</a>
<a href="telnet:18830484731">call me</a>

```

### XSS

> 木马和蠕虫

#### 反射型

#### 存储型

#### DOM型

<https://github.com/component/escape-html>

### SQL注入

> SQL字段约束: 非空(NOT NULL)、默认值(DEFAULT)、主键(PRIMARY KEY)、唯一的(UNIQUE)和外键(FOREIGN KEY)

```sql
# ...
-- ...
/* ... */

CREATE DATABASE DB;

```


### CSRF

<https://github.com/helmetjs/helmet>


### 文件上传和包含

[获取本机外网IP](https://ip.900cha.com/)

### 网站攻击

#### DDOS攻击

## 子资源完整性

一种前端安全机制，用于确保从外部加载的资源（如 JavaScript、CSS 文件等）未被篡改。它通过验证资源的哈希值来保证其完整性

使用`openssl`生成哈希值:

```sh
openssl dgst -sha384 -binary example.js | openssl base64 -A

```

```html
<script 
  src="https://example.com/example.js"
  integrity="sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho1wx4JwY8wC"
  crossorigin="anonymous">
</script>

```

Node端实现文件的`sha384`哈希加密:

```js
const crypto = require('crypto')
const fs = require('fs')

const filePath = 'example.txt'

// 创建 SHA-384 哈希对象
const hash = crypto.createHash('sha384');

// 创建文件读取流
const fileStream = fs.createReadStream(filePath);

// 监听数据流，更新哈希对象
fileStream.on('data', (chunk) => {
  hash.update(chunk);
});

// 文件读取完成后，计算哈希值
fileStream.on('end', () => {
  const hexHash = hash.digest('hex');
  console.log('SHA-384 Hash of file (hex):', hexHash);

  const base64Hash = hash.digest('base64');
  console.log('SHA-384 Hash of file (base64):', base64Hash);
})

fileStream.on('error', (err) => {
  console.error('Error reading file:', err)
})

```





## 渗透测试
