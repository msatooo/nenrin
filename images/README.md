# images/

LP で使う画像を置く場所です。

## アプリアイコン（設置済み）

ヒーロー中央のアプリアイコン。iOS アプリの実素材を使っています。

| ファイル | 用途 |
| --- | --- |
| `appicon-iOS-Default-1024x1024@1x.png` | 原本（`ios-app/design-assets/icon/appicon Exports/` からの複製）|
| `app-icon-396.png` | 実表示用（132px @3x）|
| `app-icon-264.png` | 実表示用（132px @2x）、favicon / apple-touch-icon |

原本は 2.4MB あり 132px 表示には過大なので、`sips` で縮小した 2 つを
`srcset` で出し分けています。原本は 1024w として srcset に残してあり、
参照元としても保持しています。

差し替え時は原本を上書きしたうえで、縮小版を作り直してください。

```sh
sips -Z 396 appicon-iOS-Default-1024x1024@1x.png --out app-icon-396.png
sips -Z 264 appicon-iOS-Default-1024x1024@1x.png --out app-icon-264.png
```

この PNG は四隅の alpha が 0 で iOS の角丸マスクが焼き込み済みです。
そのため CSS 側で `border-radius` は当てず、影も矩形にならないよう
`filter: drop-shadow()` を使っています（`box-shadow` にすると
四角い影が出ます）。

## Download_on_the_App_Store_Badge_JP_RGB_blk_100317.svg（設置済み）

Apple 公式の日本語 App Store バッジ（黒）。原寸 108.85×40 を
147×54 で表示しています。バッジ自身が地色と角丸を持つため、
CSS 側で背景・角丸は付けていません。

## ss01.png / ss02.png / ss03.png（設置済み）

「使い方」3ステップのスクリーンショット（原本 1206×2622）。

| ファイル | ステップ |
| --- | --- |
| `ss01.png` | 01 大切なひとを登録する |
| `ss02.png` | 02 年齢ごとに写真を刻む |
| `ss03.png` | 03 年輪をたどる（成長動画）|

表示は幅 226px の端末フレーム内（`object-fit: cover`・角丸 32px）。
原本は 1MB〜2.5MB と過大なので、`sips` で縮小した表示用の
`-452`（@2x）/`-720`（@3x）を作り、`srcset` で出し分けています。
原本は差し替え時の元素材として保持します。

```sh
for n in 01 02 03; do
  sips -Z 452 ss$n.png --out ss$n-452.png
  sips -Z 720 ss$n.png --out ss$n-720.png
done
```

差し替え時は原本を上書きし、上記コマンドで縮小版を作り直してください。

**注意：** このサイトは GitHub Pages で一般公開されます。
`nenrin/screenshot/` の既存スクリーンショットには実在の人物写真が
写っている可能性があるため、そのまま転用せず、公開してよい
ダミーデータのスクリーンショットを使用してください。
