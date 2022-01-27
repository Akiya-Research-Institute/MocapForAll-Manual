# 共有メモリへの出力

キャプチャした体の動きと表情の生データを共有メモリに出力することができます。

## 出力の有効化

- 「Settings > Data export > Shared Memory > Export to shared memory」をオンにします。

!!! Info "出力先の共有メモリ名の変更"
    「Settings > Data export > Shared Memory > Names of shared memories」に設定した名前の共有メモリに、データが書き出されます。

## 出力データフォーマット

- 最初の1バイトは、データが更新される度に+1される（255の次は0に戻る）カウンタです。
- 次の4バイトは、残りのデータのバイト単位での長さをint型で表した値です。
- 残りは、4バイトのfloat型が繰り返されます。

### Body

![](../../images/DataFormat-SharedMemory-Body.png){ loading=lazy }

### Hand

Bodyのデータと同様の形式で15個のボーンの向きと位置が出力されます。ボーンの並びは下記の通りです。

![](../../images/DataFormat-SharedMemory-Hand.png){ loading=lazy }

### Face

468個の顔のランドマークについて、位置情報のみが出力されます。位置は、顔の範囲にトリミングされたカメラ画像中でのピクセル単位でのXY座標に加え、それと同じスケールでの奥行方向の推定位置をZ座標とした3次元の値で表されます。

![](../../images/DataFormat-SharedMemory-Face1.png){ loading=lazy }

各ランドマークが顔のどこに対応するかは、下記画像を拡大して確認してください。

![](../../images/DataFormat-SharedMemory-Face.jpg){ loading=lazy }

### Eye

Faceのデータと同様の形式で、瞳について5点、まぶたについて71点の位置情報が出力されます。

## 共有メモリからの値の取得の実装例

共有メモリに書き込まれたデータをUnityで読み取りGameObjectに反映するサンプルプロジェクトを[こちらで公開しています。](https://github.com/Akiya-Research-Institute/MocapForAll-SharedMemory-Plugin-for-Unity)
