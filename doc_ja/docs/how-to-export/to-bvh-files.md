# BVH形式での書き出し

![](../../images/Settings-DataExport-BVH.gif){ loading=lazy }

- キャプチャを停止します。
- VRMファイルをMocapForAllのウィンドウにドラッグ&ドロップします。
- 「Settings > Data export > Record to BVH file」を有効にします。
- 「Start capture」をクリックすると、BVH形式でのデータ保存が開始されます。
- 「Stop capture」をクリックすると、最終的なBVHファイルが生成されます。
    - 無料試用版の場合は、300フレーム経過時点で自動的にBVHファイルが生成され、データ保存が停止されます。

!!! Info "ボーン構造はVRM準拠"
    MocapForAll上でVRMモデルにアニメーションをリターゲットした上で、BVH形式でアニメーションをエクスポートするしくみとしています。  
    そのため、BVH形式でのデータ書き出し時は、自動的にVRMを使用するモードに切り替わります。

!!! Info "VRMモデルを持っていない場合"
    VRMモデルをお持ちでない場合は、実際にモデルをロードせずに、「Settings > General > Character」で「VRM runtime load」を選択してください。  
    ダミーのVRMモデルがバックグラウンドで使用されます。

!!! Info "長さの単位はメートル"
    生成されるBVHファイルのボーンの長さの単位はメートルとしています。読み込み先のアプリケーションで単位を適切に設定してください。