---
title: VRChatへの連携
---

# VRChatへの連携

VRChatの[OSC Tracker](https://docs.vrchat.com/docs/osc-trackers)として関節位置を出力し、VRChatでFull-body Trackingに使用できます。

!!! Warning "OSC Trackerはβ機能です"
    2023年2月1日現在、OSC TrackerはVRChatの正式リリース機能ではなく、正常に動作することは保証されていません。  
    詳細はVRChatのページをご覧ください。  
    参考：[OSC Overview](https://docs.vrchat.com/docs/osc-overview)

## 基本的な送信設定

![](../../images/Settings-VRChatOSC.png){ loading=lazy }

- 「Settings > Data export > VRChat OSC (β)」をオンにし、「Dest. IP address」を下記の通り設定します。
    - 送信先が同じPCの場合：「127.0.0.1」
    - 送信先が別のデバイス（例：Quest2）の場合： 送信先デバイスのIPアドレス

## VRChat側での位置合わせ

[VRChatのこちらのドキュメント](https://docs.vrchat.com/docs/osc-trackers#auto-center-osc-trackers)に記載の通り、「Auto-center OSC Trackers」を押すことで自動で位置合わせができます。  
このボタンは、VRChatがOSCでデータを受信しているときしか表示されないことに注意してください。

## 関節の選択

- 「Settings > Data export > VRChat OSC (β)」以下の各関節をオンオフすることで、送信する関節位置を選択できます。
- 「Tracker index」で各関節をどの番号で送るかを選択できます。

!!! Tip "頭との相対位置で動かす"
    「Tracker index」を「0」にすると、「/tracking/trackers/head」としてその関節位置が送信されます。  
    （デフォルトでは、index=0は頭関節に指定されています）  
    これは、ヘッドマウントディスプレイとの相対位置で各関節を動かしたい場合に使用します。  

    - この機能を使用すると、MocapForAll上での頭と各部位の相対位置が、ヘッドマウントディスプレイと各部位の相対位置に変換されて仮想トラッカーの位置に使われます。  
      ヘッドマウントディスプレイに対して、各部位の仮想トラッカーの位置情報の**遅延が目立ちにくくなります**が、例えば歩き出しは、頭に連れて各部位が横滑りするような見た目になります。

    - この機能を使用しない場合、各部位の実際のトラッキング位置がそのまま各部位の仮想トラッカーの位置として使われます。
      ヘッドマウントディスプレイに対する、各部位の仮想トラッカーの位置情報の**遅延がそのまま見えてしまう**状態になります。  
      例えば歩き出しは、頭だけが先行し、残りの部位が後からついてくるような見た目になります。

    なお、この機能は頭の向きに基づいて、VRChatとMocapForAllのトラッキング座標の向きを自動で合わせることも同時に行います。  
    これが正しく機能するためには、MocapForAllの頭のトラッキングの**向きのオフセットに Z=90 を指定**する必要があります。  
    この値はデフォルトで指定済みです。

    ![](../../images/Settings-VRChatOSC-Head.png){ loading=lazy }

    詳細は[VRChatのこちらのドキュメント](https://docs.vrchat.com/docs/osc-trackers#receiving-head-data)をご覧ください。