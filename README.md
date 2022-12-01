# btpanel-v7.7.0
btpanel-v7.7.0-backup  官方原版v7.7.0版本面板备份

**Centos/Ubuntu/Debian安装命令 独立运行环境（py3.7）**

```Bash
curl -sSO https://raw.githubusercontent.com/doublog/btpanel-v7.7.0/main/install/install_panel.sh && bash install_panel.sh
```

# 手动破解：

1，屏蔽手机号

```
sed -i "s|bind_user == 'True'|bind_user == 'XXXX'|" /www/server/panel/BTPanel/static/js/index.js
```

2，删除强制绑定手机js文件

```
rm -f /www/server/panel/data/bind.pl
```

3，手动解锁宝塔所有付费插件为永不过期

文件路径：`/www/server/panel/data/plugin.json`

搜索字符串：`"endtime": -1`全部替换为`"endtime": 999999999999`

4，给plugin.json文件上锁防止自动修复为免费版

```
chattr +i /www/server/panel/data/plugin.json
```

============================

！！如需取消屏蔽手机号
```
sed -i "s|if (bind_user == 'REMOVED') {|if (bind_user == 'True') {|g" /www/server/panel/BTPanel/static/js/index.js
```

5,命令行bt出现如下错误时
```
root@debian:~# bt
Traceback (most recent call last):
  File "/www/server/panel/tools.py", line 688, in <module>
    bt_cli(clinum)
  File "/www/server/panel/tools.py", line 431, in bt_cli
    print("===============\u5b9d\u5854\u9762\u677f\u547d\u4ee4\u884c==================")
UnicodeEncodeError: 'latin-1' codec can't encode characters in position 15-21: ordinal not in range(256)
```
是py环境变量的原因
可以通过运行以下代码解决：

```
export PYTHONIOENCODING=utf-8
```


特别鸣谢 8838 大佬
-
[https://github.com/8838](https://github.com/8838)

