---
title: VMC互換アプリへの連携
---

# VMCプロトコル対応アプリへの連携

VMCプロトコルを介して、様々なアプリケーションに情報を連携することができます。動作確認済みのアプリケーションは下記の通りです。

- [VSeeFace](https://www.vseeface.icu/)へのボーンの送信、VSeeFaceからの表情モーフの受信
- [EVMC4U](https://github.com/gpsnmeajp/EasyVirtualMotionCaptureForUnity)へのボーンと表情モーフの送信
- [VMC4UE](https://github.com/HAL9HARUKU/VMC4UE)へのボーンと表情モーフの送信
- [VMC4B](https://tonimono.booth.pm/items/3432915)へのボーンの送信
- [VirtualMotionCapture](https://vmc.info/)へのトラッカーの送信

!!! Question "VMCが必要?"
    ここで説明している「VMCプロトコル」でのアプリケーション間の通信には、「VMC」それ自体は基本的に不要です。  
    （VirtualMotionCaptureは、VMCプロトコルでの通信に対応したアプリケーションの**代表例の一つ**であると捉えてください）

## VRMモデル読み込み

- キャプチャを停止します。
- VRMファイルをMocapForAllのウィンドウにドラッグ&ドロップします。

!!! Info "注意"
    宛先のアプリと同じVRMモデルを読み込んでください。

!!! Question "直接モードと間接モード"
    直接モードをまず試してください。間接モードは直接モードで動作しないモデルのための回避策です。

![](../../images/Settings-General-Character-VRM.gif){ loading=lazy }

## 送信設定

![](../../images/Settings-DataExport-VMC.png){ loading=lazy }

- 「Settings > Data export > Destination IP address for VMT and VMC」を下記の通り設定します
    - 送信先が同じPCの場合：「127.0.0.1」
    - 送信先が別のPCの場合： 送信先のデバイスのIPアドレス
- 「Settings > Data export > VMC protocol > Send bones」をオンにします
- 「Settings > Data export > VMC protocol > Send bones」のポートを、送信先のポートに合わせて設定します

??? Tip "トラッカーとして送信"
    ボーン（/VMC/Ext/Bone/Pos）としてではなく、トラッカー（/VMC/Ext/Tra/Pos）としてデータを送信したい場合は、下記を設定します。  
    （例えば、VirtualMotionCaptureにデータを送信するにはこの設定が必要です）

    - 「Settings > Data export > VMC protocol > Send bones > As trackers (/VMC/Ext/Tra/Pos) 」をオンにします

## 表情の受信・送信

表情モーフデータを受信するには、下記の通り設定します。

- 「Settings > Data export > VMC protocol > Receive facial morphs」をオンにします
- 「Settings > Data export > VMC protocol > Receive facial morphs」のポートを、送信元のアプリが指定している送信先ポートに合わせて設定します
- 「Settings > Data export > VMC protocol > Receive facial morphs > From other device」を下記の通り設定します。
    - 送信元が同じPCの場合：オフ
    - 送信元が別のデバイスの場合：オン

受信した表情モーフデータは、[送信設定](#_1)がされていれば、そのまま送信されます。