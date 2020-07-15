# 索引碎片

> 在长期的数据更改过程中，索引文件和数据文件，都会产生空洞和碎片，会降低索引的运行效率

## 查看碎片

```text
SHOW TABLE STATUS LIKE '表名';
```

## 修复方法

```text
alter table xxx engine innodb/myisam
```

例如之前表的引擎是innodb，执行 alter table xxx engine innodb ，还是可以起到修复碎片作用的

