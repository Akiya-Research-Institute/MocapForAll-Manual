# SteamVRへの連携

gpsnmeajp様が作成した「[Virtual Motion Tracker](https://gpsnmeajp.github.io/VirtualMotionTrackerDocument/)(VMT)」と組み合わせて使用することで、MocapForAllでキャプチャした結果を仮想トラッカーとしてSteamVRで使用することができます。  
仮想トラッカーを用いることで、例えばVRChatでフルボディトラッキングを実現することができます。 

!!! Warning "重要"
    VMT は MocapForAll とは別のプログラムであることに注意してください。VMT と MocapForAll を一緒に利用して発生したいかなる問題についても、VMT の作者様に問い合わせしないでください。

## VMTのインストール

- [ここからダウンロードします。](https://github.com/KenjiAsaba/VirtualMotionTracker/releases)
- VMTの[公式セットアップ手順](https://gpsnmeajp.github.io/VirtualMotionTrackerDocument/setup/)にしたがい、インストールします。

!!! Question "どのバージョンのVMTを使うか"
    後述の[SteamVRとMocapForAllの座標合わせ](#steamvrmocapforall)で自動調整機能を使う場合は、VMT は MocapForAll 向けに改造したバージョンを使用する必要があります。  
    手作業で座標合わせを行う場合は、上記バージョンを使用する必要はありません。vmt_011以上を使用してください。vmt_013cの使用をおすすめします。

!!! Info "トラッカーが使用するアプリで機能しない場合"
    一部のアプリケーションでVMTを利用するには、[コントローラーバンディングの設定](https://gpsnmeajp.github.io/VirtualMotionTrackerDocument/advanced/#how-to-set-the-controller-bainding)を行う必要があります。

!!! Info "VMTがうまく動作しない場合"
    まずは、[公式のトラブルページ](https://gpsnmeajp.github.io/VirtualMotionTrackerDocument/trouble/)を見てみることをおすすめします。

## VMTへの送信設定

![](../../images/Settings-DataExport-VMT-SteamVR.png){ loading=lazy }

- 「Settings > Data export > Destination IP address for VMT and VMC」を下記の通り設定します
    - 送信先が同じPCの場合：「127.0.0.1」
    - 送信先が別のPCの場合： 送信先のPCのIPアドレス
        - コマンドプロンプトを開いて、"ipconfig /all" で確認できます
        - MocapForAllとSteamVRを別PCで実行することで、処理の負荷を分散させ、快適にVRゲームをプレイすることができます
- 「Settings > Data export > VMT protocol > Send tracking points」をオンにします
- 「Settings > Data export > VMT protocol > Send tracking points」のポートを「39570」にします
- 「Settings > Data export > VMT protocol > Send tracking points > Tracking points to be sent」の下の必要な箇所をオンにします
    - 例えばVRChatで使用する場合は、「Pelvis」と「Feet」をオンにします
    - それぞれの左横の「>」をクリックすると、仮想トラッカー位置のオフセットを調整できます。

!!! Info "頭との相対位置を使うか"

    下記設定については、好みに応じてオンオフを決定してください。まずはオンで試し、動きにこだわりたい場合にオフを試すことをおすすめします。

    - `Settings > Data export > VMT protocol > Send tracking points > As relative position to HMD`

        - **オフ**にすると、各部位の実際のトラッキング位置が、そのまま各部位の仮想トラッカーの位置として使われます。
            - ヘッドマウントディスプレイに対する、各部位の仮想トラッカーの位置情報の**遅延がそのまま見えてしまう**状態になります。  
            (例えば歩き出しは、頭だけが先行し、残りの部位が後からついてくるような見た目になります)
            - 後述の[SteamVRとMocapForAllの座標合わせ](#steamvrmocapforall)で、**スケールと位置を適切に設定**する必要があります。
            (スケールが一致していない場合、部屋の中での移動に応じてヘッドマウントディスプレイと各部位の水平方向の位置がずれます)

        - **オン**にすると、頭と各部位の相対位置が、ヘッドマウントディスプレイと各部位の相対位置に変換されて仮想トラッカーの位置に使われます。
            - ヘッドマウントディスプレイに対して、各部位の仮想トラッカーの位置情報の**遅延が目立ちにくくなります**。  
            (例えば歩き出しは、頭に連れて各部位が横滑りするような見た目になります)
            - 後述の[SteamVRとMocapForAllの座標合わせ](#steamvrmocapforall)で、**スケールは適当でOK、位置の設定は不要**になります。

## SteamVRとMocapForAllの座標合わせ

SteamVRでトラッキングされているHMDおよびコントローラの座標系と、MocapForAllでトラッキングされている体の位置の座標系は、そのままでは一致しません。これらを一致させるよう、手動または自動で調整する必要があります。

=== "自動調整"
    
    !!! Info "前提条件"
        [VMTのインストール](#vmt)に記載の通り、MocapForAll向けに改造したバージョンのVMTを使用する必要があります。  

    - VMT Manager および 他のポート39571を使用するアプリを終了します。
    - 「Settings > Data export > VMT protocol > Send tracking points」をオンにします。
    - ヘッドマウントディスプレイを被り、SteamVRが起動している状態にします。
    - SteamVRとMocapForAllの両方でトラッキングが成立する位置に立ちます。
    - MocapForAllで、ウィンドウ上部の「Align coord. to VR」をクリックします。
    - 適当に歩き回ります。しばらくすると、自動的に「Settings > Coordinates」の値が更新され、SteamVRとMocapForAllの座標が一致した状態になります。

    ![](../../images/Settings-DataExport-VMT-SteamVR-Align.gif){ loading=lazy }  

=== "手動調整"
    - 準備
        - MocapForAll ウィンドウ上部の「Start capture」をクリックし、モーションのキャプチャを開始します。
        - ヘッドマウントディスプレイを被り、SteamVR Homeを含むSteamVRで動いているアプリを終了し、SteamVRのデフォルト画面で仮想トラッカーを視認できる状態にします。

    - スケールの調整
        - MocapForAllで
            - 「Settings > Data export > VMT protocol > Send tracking points > Tracking points to be sent」の下の「Head」をオンにします。
            - 「Settings > Data export > VMT protocol > Send tracking points > As relative position to HMD」をオフにします。
        - 自分の目線の高さと、「Head」の仮想トラッカーの高さが一致するように、「Settings > Coordinates > Scales > Upper body」および「Settings > Coordinates > Scale > Lower body」の値を設定します。「Upper body」と「Lower body」は基本的に同じ値にします。
    
    - 回転の調整
        - MocapForAllで
            - 「Settings > Data export > VMT protocol > Send tracking points > Tracking points to be sent」の下の「Feet」をオンにします。
            - 「Settings > Data export > VMT protocol > Send tracking points > As relative position to HMD」をオンにします。
        - 自分の足を前後に動かし、その動く向きが足元の「Feet」の仮想トラッカーの動く向きと一致するように、「Settings > Coordinates > Orientation offset」の値を設定します。
    
    - 位置の調整
        - MocapForAllで
            - 「Settings > Data export > VMT protocol > Send tracking points > Tracking points to be sent」の下の「Feet」をオンにします。
            - 「Settings > Data export > VMT protocol > Send tracking points > As relative position to HMD」をオフにします。

        - 自分の足の位置と「Feet」の仮想トラッカーの位置が一致するよう、「Settings > Coordinates > Position offset」の値を設定します。