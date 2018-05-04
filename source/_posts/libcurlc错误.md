---
title: Protocol https not supported or disabled in libcurl错误
date: 2018-03-19 23:35:12
tags: 
categories: tools
---

原因：Windows下不支持命令中的单引号，把url中的单引号改为双引号即可

```
curl  'http://localhost:9200/api/twittervnext/tweet'
```

改为

```
curl  "http://localhost:9200/api/twittervnext/tweet"
```


即可