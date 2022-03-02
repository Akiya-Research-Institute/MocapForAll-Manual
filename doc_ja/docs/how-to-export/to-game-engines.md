# ゲームエンジンへの連携

## 受信プラグイン

Unreal Engine 4, Unreal Engine 5, Unityでデータを受信するための[プラグインを公開しています。](https://booth.pm/ja/items/3026430)

!!! Question "VMTが必要?"
    上記のプラグインは通信にVMTプロトコルを使用していますが、VMTそれ自体やSteamVRは不要です。

### Unreal Engine向けプラグインの使い方
- [UE4版データ受信プラグインの使い方](https://github.com/Akiya-Research-Institute/MocapForAll-Receiver-Plugin-for-UE4/wiki)
- [UE5版データ受信プラグインの使い方](https://github.com/Akiya-Research-Institute/MocapForAll-Receiver-Plugin-for-UE5/wiki)

### Unity向けプラグインの使い方
- [Unity版データ受信プラグインの使い方](https://github.com/Akiya-Research-Institute/MocapForAll-Receiver-Plugin-for-Unity/blob/main/README.md)
- [Unity版データ受信プラグインの使い方(共有メモリ使用)](https://github.com/Akiya-Research-Institute/MocapForAll-SharedMemory-Plugin-for-Unity/blob/main/README.md)

## VMC4UE、EVMC4Uによる連携
- [VMC互換アプリへの連携](../to-vmc-marionette)に記載の通り、MocapForAllの設定を行います。
- VMC4UE
    - [公式Wiki](https://github.com/HAL9HARUKU/VMC4UE/wiki#ue4-の使い方)に記載の「UE4の使い方」の通りUE4の設定を行います。
    - UE4エディタで`Play`をクリックします。（最後の「VirtualMotionCapture の使い方」は不要）
- EVMC4U
    - [公式WikiのExternalReceiverPackを使う場合](https://github.com/gpsnmeajp/EasyVirtualMotionCaptureForUnity/wiki/How-to-use#externalreceiverpack%E3%82%92%E4%BD%BF%E3%81%86%E5%A0%B4%E5%90%88%E3%81%8B%E3%82%93%E3%81%9F%E3%82%93)に記載の「0. Unityを準備する」から「4. 再生して実行」を実施します。