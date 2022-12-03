## 降级到7.5.2

执行：

```
curl -sSO https://raw.githubusercontent.com/doublog/btpanel-v7.7.0/main/downgrade/down7.sh && bash down7.sh
```

干掉验证：

```
sed -i "s|if (bind_user == 'True') {|if (bind_user == 'REMOVED') {|g" /www/server/panel/BTPanel/static/js/index.js
```
