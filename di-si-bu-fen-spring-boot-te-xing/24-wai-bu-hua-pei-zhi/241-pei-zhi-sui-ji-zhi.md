## 24.1 配置随机值

RandomValuePropertySource可用于注入随机值（例如，注入密码或测试用例）。 它可以产生整数，长整数，uuids或字符串，例如

```
my.secret=${random.value}
my.number=${random.int}
my.bignumber=${random.long}
my.uuid=${random.uuid}
my.number.less.than.ten=${random.int(10)}
my.number.in.range=${random.int[1024,65536]}
```

random.int \*语法是OPEN value（，max）CLOSE，其中OPEN，CLOSE是任何字符和值，max是整数。 如果提供max，则value为最小值，max为最大值（不包含最大值）。



