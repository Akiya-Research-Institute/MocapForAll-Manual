# FBX形式での書き出し

- 「Settings > Data export > Record to FBX file」を有効にします。
- 「Start capture」をクリックすると、FBX形式でのデータ保存が開始されます。
- 「Stop capture」をクリックすると、最終的なFBXファイルが生成されます。
    - 無料試用版の場合は、300フレーム経過時点で自動的にFBXファイルが生成され、データ保存が停止されます。

!!! Info "ボーン構造はUE Mannequin準拠"
    MocapForAll上でUE Mannequinモデルにアニメーションをリターゲットした上で、FBX形式でアニメーションをエクスポートするしくみとしています。  
    そのため、FBX形式でのデータ書き出し時は、自動的にUE Mannequinモデルに切り替わります。

!!! Info "アニメーションは25fpsでベイクされます"
    MocapForAll上で25fpsの固定フレームレートでベイクした後、アニメーションをFBXフォーマットで書き出します。  

!!! Warning "顔の表情は書き出されません"
    顔の表情のエクスポートはサポートされていません。
