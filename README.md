ask.sdparty.tw
==========

社會民主黨網路審議系統

* 開發在 `gh-pages` 分支，預覽在 https://demo.sdparty.tw/
 * Please send pull requests and commits toward `gh-pages`
* 部署在 `master` 分支，會在 https://ask.sdparty.tw/
 * This require a manual merge and will take effect in 2hr (after CloudFlare cache expiry)

FB: https://www.facebook.com/sdparty
上線後繼續每周二小松更新系統，下次大幅更新（可能要另開 branch）預期在 3/1。

## 部署機的範例設定

分為兩個 process 來跑（可以跑在不同的 screen 或 rc.local 裡）：

```
perl -e while (sleep 60) { system("npm install && gulp") if `git pull 2>&1` =~ /-> origin.master/ }
env USE_HTTPS=1 forever server.js
```

然後再用 CloudFlare 的自動 SSL 連到 server 上即可。

目前正計劃加上 INDEX_URL 參數後 Dockerize。
