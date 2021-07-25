# skipBahaAD

用來跳過動畫瘋廣告

# 原理

先發出 request 到巴哈，想辦法取得看過廣告的狀態

## 巴哈 API

- 開始看廣告，
  - API:`/ajax/videoCastcishu.php?s=${s}&sn=${sn}`
- 看完廣告，須等發出"開始看廣告" 25 秒後才生效
  - API:`/ajax/videoCastcishu.php?s=${s}&sn=${sn}&ad=end`
- 確認 API。看這集有沒有看過廣告，自"開始看廣告"發出後 10 可維持 10 分鐘不須再看
  - API:`/ajax/token.php?sn=${_sn}`
  - `respond.time == 1;` 不須再看廣告
  - `respond.time == 0;` 須看廣告
  - 若取得不須再看廣告資格 在發出其他集的確認 API，會導致本集中斷
