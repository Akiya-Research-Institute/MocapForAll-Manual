# MocapForAllのインストール

BOOTH または Steam からインストールすることができます。

=== "From BOOTH"
    ## ダウンロード
    #### 無料試用版

    [Download from BOOTH](https://akiya-souken.booth.pm/items/3026474){: .md-button .md-button--primary }  

    ??? Question "無料試用版の制限"
        無料試用版では、キャプチャ結果を外部にエクスポートする機能に制限が設けられています。

        - VMTプロトコル、VMCプロトコル、共有メモリへのデータ出力は、10秒ごとに送信の停止・再開が繰り返されます
        - BVHファイルは、300フレームまでに制限されます

    #### 有料版
    購入前に、

    - 必ず[利用規約](https://vrlab.akiya-souken.co.jp/eula)を読み、同意してください。  
    - 必ず無料試用版でソフトウェアがご利用の環境で問題なく動作することをご確認ください.  

    同意いただける場合は、下記HPから購入用パスワードが入手でき、BOOTHの購入ページへお進みいただけます。  

    [Our HP](https://vrlab.akiya-souken.co.jp/product#buy){: .md-button .md-button--primary }  

    ## インストール
    手動でのインストールと、ネットーワークインストーラでのインストールの二つの方法があります。  

    === "手動インストール"

        #### 本体
        1. 「MocapForAll_Full_vN.N.N.zip」をダウンロードして展開（解凍）します。  
        2. 「MocapForAll_Full_vN.N.N」フォルダでMocapForAll.exeを実行します。  
        3. 「UE4 Prerequisites」のインストール画面が表示された場合は、インストールしてください。  

        #### 付録（省略可）

        Appendixに付属の機能が不要な場合はこの手順はスキップしてください。

        ??? Question "Appendixの機能"
            Appendixは、本体のプログラムとは分離されている"付録"の機能です。  
            Appendixは下記の4種類があります。

            - Appendix1：Precision mode  
            精度重視の「Precision」モードが使えるようになります。処理負荷が非常に高いため、VRアプリ等との併用はおすすめできません。
            - Appendix2：HDRI maps  
            [HDRI Haven](https://hdrihaven.com)の HDRI画像を背景に用いたいくつかのマップを追加します。MocapForAll単独で動かして遊ぶ（そんな用途あるかしら？）のに使えるかもしれません。
            - Appendix3：MetaHuman character  
            Epic Games の MetaHuman Creator によって作成されたキャラクターを追加します。MocapForAll上でのキャプチャ精度の確認に使用します。
            - Appendix4：TensorRT mode（非推奨）  
            TensorRTによるGPUアクセラレーション機能を追加します。後述の通りCUDA, cuDNN, TensorRTを別途インストールする必要があります。多くの人は、標準装備のDirectMLで事足りると思います。  
            この機能は、パフォーマンスの向上が非常に小さいことが多く、場合によってはむしろ悪化することがあり、また、正常に動作するかはユーザの環境に依存するため、非推奨になっています。

        1. 「AppendixN_xxxxx_yyyyy.zip」をダウンロードして展開します。 
        2. 「MocapForAll_Full_vN.N.N\MocapForAll」を「AppendixN_xxxxx_yyyyy\MocapForAll」で上書きします。  
        3. 「Appendix4_TensorRT_mode」を使用する場合は、[TensorRTのインストール](../install-tensorrt)を行います。


    === "ネットーワークインストーラでのインストール"
        1. 「Network_Installer_-_MocapForAll_Full_vN.N.N.zip」をダウンロードして解凍します。
        2. 「Network_Installer_-_MocapForAll_Full_vN.N.N.exe」を実行します。
        3. 必要なAppendixを選択します。
    
            ??? Question "Appendixの機能"
                Appendixは、本体のプログラムとは分離されている"付録"の機能です。  
                Appendixは下記の4種類があります。

                - Appendix1：Precision mode  
                精度重視の「Precision」モードが使えるようになります。処理負荷が非常に高いため、VRアプリ等との併用はおすすめできません。
                - Appendix2：HDRI maps  
                [HDRI Haven](https://hdrihaven.com)の HDRI画像を背景に用いたいくつかのマップを追加します。MocapForAll単独で動かして遊ぶ（そんな用途あるかしら？）のに使えるかもしれません。
                - Appendix3：MetaHuman character  
                Epic Games の MetaHuman Creator によって作成されたキャラクターを追加します。MocapForAll上でのキャプチャ精度の確認に使用します。
                - Appendix4：TensorRT mode（非推奨）  
                TensorRTによるGPUアクセラレーション機能を追加します。後述の通りCUDA, cuDNN, TensorRTを別途インストールする必要があります。多くの人は、標準装備のDirectMLで事足りると思います。  
                この機能は、パフォーマンスの向上が非常に小さいことが多く、場合によってはむしろ悪化することがあり、また、正常に動作するかはユーザの環境に依存するため、非推奨になっています。  
                これを使用する場合は、「[TensorRTのインストール](../install-tensorrt)」を参照し、必要なソフトウェアをインストールしてください。

        4. スタートメニューからMocapForAllを実行するか、インストールパスでMocapForAll.exeを実行します。

        5. 「UE4 Prerequisites」のインストール画面が表示された場合は、インストールしてください。


    ## アップデート

    手動、または、ネットーワークインストーラでアップデートできます。

    === "手動アップデート"

        1. 「MocapForAll_Full_vN.N.N.zip」をダウンロードして展開（解凍）します。  
        2. 「MocapForAll_Full_vN.N.N」で、古いバージョンの「MocapForAll_Full_vM.M.M」を上書きします。

    === "ネットーワークインストーラでのアップデート"

        インストール時と同じです。

        !!! Tip "ダウンロードのデータ量の削減"
            ダウンロードするデータ量を削減したい場合は、インストーラの「Select Components」画面でAppendixは特に選択せず「Main Files」のみを選択し、インストールを実行します。  
            インストーラではファイルの削除は行わないので、以前のAppendixは残っている状態です。  
            これ以降、インストーラの「Select Components」画面ではAppendixがインストールされていない扱いになりますが、問題ありません。

=== "From Steam"

    デモ版と有料版があります。  
    有料版の購入前に、  

    - 必ず[利用規約](https://store.steampowered.com//eula/1759710_eula_0)を読み、同意してください。  
    - 必ずデモ版でソフトウェアがご利用の環境で問題なく動作することをご確認ください.  

    [Go to Steam store](https://store.steampowered.com/app/1759710/MocapForAll/){: .md-button .md-button--primary } 

    ??? Question "デモ版の制限"
        デモ版では、キャプチャ結果を外部にエクスポートする機能に制限が設けられています。

        - VMTプロトコル、VMCプロトコル、共有メモリへのデータ出力は、10秒ごとに送信の停止・再開が繰り返されます
        - BVHファイルは、300フレームまでに制限されます

    !!! Question "Appendix"

        すべての**Appendix**が自動的にインストールされます。 

        ??? Question "Appendixの機能"
            Appendixは、もともとは本体のプログラムとは分離されていた"付録"の機能です。  
            Appendixは下記の4種類があります。

            - Appendix1：Precision mode  
            精度重視の「Precision」モードが使えるようになります。処理負荷が非常に高いため、VRアプリ等との併用はおすすめできません。
            - Appendix2：HDRI maps  
            [HDRI Haven](https://hdrihaven.com)の HDRI画像を背景に用いたいくつかのマップを追加します。MocapForAll単独で動かして遊ぶ（そんな用途あるかしら？）のに使えるかもしれません。
            - Appendix3：MetaHuman character  
            Epic Games の MetaHuman Creator によって作成されたキャラクターを追加します。MocapForAll上でのキャプチャ精度の確認に使用します。
            - Appendix4：TensorRT mode（非推奨）  
            TensorRTによるGPUアクセラレーション機能を追加します。後述の通りCUDA, cuDNN, TensorRTを別途インストールする必要があります。多くの人は、標準装備のDirectMLで事足りると思います。  
            この機能は、パフォーマンスの向上が非常に小さいことが多く、場合によってはむしろ悪化することがあり、また、正常に動作するかはユーザの環境に依存するため、非推奨になっています。

        TensorRTによるGPUアクセラレーションを使用するには、手動で[CUDA、cuDNN、およびTensorRTをインストール](../install-tensorrt)する必要があります。