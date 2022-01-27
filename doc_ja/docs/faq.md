# FAQ

## カメラが認識されません
- [カメラ制御フレームワークの選択](../how-to-capture/calibrate-cameras/connect-cameras/#_3)で、UE4 media playerを選択します
    - Image sizeから、異なるフォーマットを指定してみてください
- カメラ制御フレームワークの選択で、Direct Showを選択します
    - カメラの仕様に基づき、適切なImage sizeを指定してください

いずれでも動作しない場合、残念ですがMocapForAllでそのカメラは使用できません。

## 同機種のカメラ複数が認識されません
同機種のカメラをPCに接続する場合、アプリ内のカメラ選択のプルダウン内に一部のカメラが表示されない（検出されない）問題があります。その場合は表示されないカメラデバイスにレジストリエディタから任意のFriendlyNameを設定すると認識される可能性があります。  
FriendlyNameの設定・変更の方法はお使いの環境により異なるため、検索等で各自お調べください。レジストリの書き換えとなるため、バックアップを取るなどの対策をお勧めします。  

## 仮想カメラが認識されません
OBSに標準で入っている仮想カメラは機能しないことがわかっています。[OBS-VirtualCamプラグイン](https://obsproject.com/forum/resources/obs-virtualcam.539/)をインストールし、[カメラ制御フレームワークの選択](../how-to-capture/calibrate-cameras/connect-cameras/#_3)で、Direct Showを選択してください。

## モノクロのカメラは使えますか
いいえ、このアプリではモノクロのカメラは使用できません。RGBカメラをご使用ください。  

## ARマーカが認識されません
- [カメラの画像が鏡像になっていないことを確認してください。](../how-to-capture/calibrate-cameras/connect-cameras)
- カメラの画像がARマーカに対してフォーカスが合っていることを確認してください。
- カメラの画像内でARマーカが十分に大きく映っていることを確認してください。
    - ARマーカのサイズを大きく印刷すると解決するかもしれません
    - 外部パラメータのカメラ校正においては、[マーカをうまく読み取れない場合](../how-to-capture/calibrate-cameras/execute-calibration/#_4)を参照してください。

## 外部パラメータのカメラ校正がうまくいきません
[マーカをうまく読み取れない場合](../how-to-capture/calibrate-cameras/execute-calibration/#_4)を参照してください。

## カメラ校正をしてもモーションキャプチャができません
- キャプチャ開始時点は人が真っすぐ立っている画像でなければ認識できません。[カメラの設置状況に合わせてカメラ画像を適切に回転してください。](../how-to-capture/calibrate-cameras/connect-cameras)
- カメラ校正が完了した二つ以上のカメラから全身が映ることを確認してください。
- 最終的なフレームレートが 4FPS 以下の場合、動作しません。[フレームレートを確認](../how-to-capture/adjust-settings/optimize-performance/#_2)してください。

## 複数人のキャプチャに対応していますか？
いいえ、現在のところ1名のみのトラッキングが可能です。そのためカメラには原則1名のみが映るようにしてください。  

## VMTが動きません
VMT Managerでエラーを確認してください。特に、[Room Matrixの設定](https://gpsnmeajp.github.io/VirtualMotionTrackerDocument/trouble/#room-matrix-is-not-set)がされているか確認してください。

## VMTの動きがおかしいです

[SteamVRとMocapForAllの座標合わせ](../how-to-export/to-steamvr/#steamvrmocapforall)が適切にされているか確認してください。

## シリアルナンバーの入力欄がありません
最新のMocapForAllをインストールしてください。バージョン1.0以降からHMDのシリアルナンバー入力は不要です。  

## MocapForAllと他のツールとの違い
- [OpenPose](https://github.com/CMU-Perceptual-Computing-Lab/openpose/blob/master/doc/advanced/3d_reconstruction_module.md)： 基本的な実装方針は近いですが、ライセンスが大きく異なります。OpenPoseは基本的に"ACADEMIC OR NON-PROFIT ORGANIZATION NONCOMMERCIAL RESEARCH USE ONLY"です。