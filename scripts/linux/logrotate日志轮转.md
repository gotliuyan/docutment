# logrotate 日志轮转

> 以mycat wrapper.log 为例

> mycatwrapper.conf 

```bash
/opt/mycat/logs/wrapper.log {
    daily
    #每天轮转一次
    rotate 4
    # 保留4次，也就是4天的日志
    compress
    # 压缩日志
    maxage 15
    # 删除超过15天的日志
    minsize 1G

}
```