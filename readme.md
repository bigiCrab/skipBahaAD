# skipBahaAD

用來跳過動畫瘋廣告
使用需安裝 chrome 插件 violentmonkey
技術分享，腳本沒有上架到greasyfork，免費仔還是要乖乖看廣告阿~

## 效果

進入動畫播放頁時，幫你播放這集與下一集的廣告，無法一進入頁面就沒廣告。
可以先把要看的動畫分頁開好，之後要看的時候就不會有廣告了。

## 找出的巴哈 API

- 開始看廣告，
  - API:`/ajax/videoCastcishu.php?s=${s}&sn=${sn}`
- 看完廣告，須等發出"開始看廣告" 25 秒後才生效
  - API:`/ajax/videoCastcishu.php?s=${s}&sn=${sn}&ad=end`
- 確認 API。看這集有沒有看過廣告，自"開始看廣告"發出後 10 可維持 10 分鐘不須再看
  - API:`/ajax/token.php?sn=${_sn}`
  - `respond.time == 1;` 不須再看廣告
  - `respond.time == 0;` 須看廣告
  - 若取得不須再看廣告資格 在發出其他集的確認 API，會導致本集中斷
