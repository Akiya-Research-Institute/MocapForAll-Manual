# 手と顔のキャプチャ

- 「Settings > General > Capture hand」をオンにすると、指の動きをキャプチャします
- 「Settings > General > Capture face」をオンにすると、顔の表情をキャプチャします

上記はいずれも実験的な機能です。処理負荷が高いこと、精度が低いことに注意してください。

## キャプチャ時のトリミングのサイズ

「Settings > Advanced > Cropping size for hand」と「Cropping size for face」から、手と顔のキャプチャ時に画像を切り抜いてAIへの入力とする際のサイズを設定できます。人によって手や顔の大きさが異なるため、この値を調整すると精度が向上することがあります。

## 手のキャプチャの動作モード

「Settings > General > Capture hand」の右のプルダウンから、動作モードを変更できます。

- 「Full」：処理負荷が少し高く、精度が高いモードです。
- 「Lite」：処理負荷が少し低く、精度が低いモードです。
- 「Legacy」：v1.13以前に使用していたAIで動作します。後方互換のためのものです。

## 顔のモーフターゲット名の設定

VRM モデルを使用している場合にのみ、顔のモーフターゲット名を指定することができます。

- 「Settings > Advanced > Specify facial morph target names」をオンにします
- 各モーフターゲットの名前を入力します。