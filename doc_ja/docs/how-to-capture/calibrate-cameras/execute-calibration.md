# カメラ校正の実施

## 内部パラメータの取得

- [この画像](https://raw.githubusercontent.com/Akiya-Research-Institute/MocapForAll-Wiki/main/resources/calibration/IntrinsicCalibration.png)を任意のアプリで画面にできるだけ大きく表示します。
- MocapForAllで「Camera > Calibration > Intrinsic」の下の「Start」ボタンをクリックします。  
- 10秒間程度、さまざまな角度からカメラで画像を写してください。カメラを固定済みの場合は、カメラでなく画像の方を動かします。  

カメラ校正が完了すると、アプリの画面上に内部パラメータが表示され、「Intrinsic  ☑Calibrated」となります。

![](../../images/Camera-Calibration-Intrinsic-Execution.gif){ loading=lazy }

完了したら「Save」からカメラ校正結果を保存しておきます。

## 外部パラメータの取得

先に説明した[外部パラメータの取得の4つの方式](../what-is-camera-calibration/#4)により、手順が異なります。

=== "ChArUcoボードを使うやり方  "
    - [外部パラメータの取得で使う画像の印刷](../prepare-markers/#_3)で印刷した画像を床に置きます。これがモーションキャプチャの原点になります。   
    - 床に置いた画像が見える場所にカメラを設置します。  
    - MocapForAllで「Settings > Calibration > Extrinsic calibration method」で「**ChArUco board (default)**」を選択します。
    - 「Camera > Calibration > Extrinsic」の下の「Start」ボタンをクリックします。
    
    キャリブレーションが完了すると、外部パラメータが表示され、「Extrinsic  ☑Calibrated」となります。
 
    !!! Tip "マーカの読み取りがうまく実施できない場合は、[マーカをうまく読み取れない場合](#_4)を試してみてください。"

    ![](../../images/Camera-Calibration-Extrinsic-Execution-Charuco.gif){ loading=lazy }
    
=== "ArUcoクラスターを使う方法 "
    -     [外部パラメータの取得で使う画像の印刷](../prepare-markers/#_3)で印刷した画像を床に置きます。「arucoMarker0.png」がモーションキャプチャの原点になります。  
    - 床に置いた画像が見える場所にカメラを設置します。  
    - MocapForAllで「Settings > Calibration > Extrinsic calibration method」で「**ArUco cluster**」を選択します。
    - 「Camera > Calibration > Extrinsic」の下の「Scan markers」ボタンをクリックします。マーカの位置関係がスキャンされ、しばらくすると3Dビューポート上にマーカが表示されます。
    - マーカがスキャンできたら「Stop scanning」をクリックし、次に「Start」ボタンをクリックします。
    
    キャリブレーションが完了すると、外部パラメータが表示され、「Extrinsic  ☑Calibrated」となります。
    
    !!! Tip "マーカの読み取りがうまく実施できない場合は、[マーカをうまく読み取れない場合](#_4)を試してみてください。"
    
    ![](../../images/Camera-Calibration-Extrinsic-Execution-Aruco.gif){ loading=lazy }
   
=== "Diamondクラスターを使う方法"
    - [外部パラメータの取得で使う画像の印刷](../prepare-markers/#_3)で印刷した画像を、カメラのフレームに収まる程度の距離をおいて配置します。同一平面内にある必要はありません。「diamondMarker0.png」がモーションキャプチャの原点になるので、これは床面に置きます。
    - MocapForAllで「Settings > Calibration > Extrinsic calibration method」で「**Diamond cluster**」を選択します。  
    - 任意のカメラの一つで「Camera > Calibration > Extrinsic」の下の「Scan markers」ボタンをクリックします。そのカメラで、「diamondMarker0.png」を映します。次に「diamondMarker0.png」といずれかのマーカを同時に映してしばらくその状態を維持します。しばらくすると「diamondMarker0.png」を原点としてもう一つのマーカの位置が確定し、当該マーカが3Dビューポート上に表示されます。
    - 位置が確定済みのマーカと位置が未確定のマーカについて、上記の作業を繰り返し、全マーカの位置が確定したら「Stop scanning」をクリックします。
    - 位置が確定済みのマーカが映る位置にカメラを設置し、「Camera > Calibration > Extrinsic」の下の「Start」ボタンをクリックします。 
    
    キャリブレーションが完了すると、外部パラメータが表示され、「Extrinsic  ☑Calibrated」となります。 
    
    !!! Tip "マーカの読み取りがうまく実施できない場合は、[マーカをうまく読み取れない場合](#_4)を試してみてください。"

    ![](../../images/Camera-Calibration-Extrinsic-Execution-Diamond.gif){ loading=lazy }

=== "人の動きを使う方法" 
    - 少なくとも二つのカメラが同時に人を映せるようにカメラを設置します。
    - MocapForAllで「Settings > Calibration > Extrinsic calibration method」で「**Human motion**」を選択します。  
    - ハードウェアが対応していれば、「Settings > General > Run DNN on」を「**GPU_DirectML**」にします。（AppendixのTensorRTモードをインストール済みの場合は「GPU_TensorRT」でもOKです）  
    - ハードウェアの性能が許せば、「Settings > General > Capture body」を「**Speed**」に設定します。（AppendixのPrecisionモードをインストール済みの場合は「Precision」でもOKです）
    - **ウィンドウ上部の「Start calibration」ボタン**をクリックし、全身がカメラに映る場所を歩き回ってください。  
    - カメラに同時に映る人体の関節位置からカメラの相対位置が決定され、一つ目のカメラを基準にして外部パラメータが決定されます。全カメラの外部パラメータが決定され、「Extrinsic ☑Calibrated」となります。  
    
    最後に、次に説明する[マーカをうまく読み取れない場合](#_4)と同じように、ウィンドウ上部の「Find Ground」ボタンをクリックして適当に歩きまわり、カメラの絶対位置を決定します。
    
    ![](../../images/Camera-Calibration-Extrinsic-Execution-Human.gif){ loading=lazy }

### マーカをうまく読み取れない場合
??? Tip "マーカを壁に掛けて校正を行う"
    マーカの位置がキャプチャ結果の高さゼロの面となるため、基本的にマーカは床に置くことを推奨していますが、カメラの性能や配置によっては床においたマーカを読み取ることが難しい場合があります。

    そのような場合、**マーカを壁に掛けてカメラ校正を行い、床面の位置はあとから調整**することができます。

    手順：

    - 印刷した画像を「床に置き」となっているところを「**適当な壁に掛け**」に読み替えてカメラ校正を実施します。
    - ハードウェアが対応していれば、「Settings > General > Run DNN on」を「**GPU_DirectML**」にします。（AppendixのTensorRTモードをインストール済みの場合は「GPU_TensorRT」でもOKです）  
    ハードウェアの性能が許せば、「Settings > General > Capture body」を「**Speed**」に設定します。（AppendixのPrecisionモードをインストール済みの場合は「Precision」でもOKです）
    - ウィンドウ上部の「**Find Ground**」をクリックし、全身が複数のカメラに映る場所を歩き回ります。しばらくすると、自動的に床面の位置が調整されます。

    ![](../../images/Camera-Calibration-Extrinsic-Execution-FindGround.gif){ loading=lazy }

### カメラ校正結果の確認

[マーカの準備](../prepare-markers/#_4)で正しい値を入力していれば、3Dビューポート上でカメラの位置を確認できます。  
MocapForAll上で視点を移動するには、キーボードのW・A・S・Dキーとマウスのドラッグを使用します。
<img src="../../../images/App-wasd.png" alt="App-wasd" style="zoom:50%;" />  

!!! Warning "カメラが床より下にある場合"
    カメラが床より下の位置に表示される場合がある可能性があることに注意してください。（この場合、カメラ校正が失敗しています）

## 結果の保存と読み込み
![](../../images/Camera-Calibration-Save.gif){ loading=lazy }

### 各カメラで 
カメラ校正が完了したら、「Camera > Calibration > Intrinsic」と「Extrinsic」の下の「Save」から、各カメラの校正結果を保存しておきます。保存した結果は「Load」から読み込むことができます。

### 全カメラまるごと
ウィンドウ上部の「Save All Cameras」ボタンと「Load All Cameras」ボタンをクリックして、カメラ設定全体を保存およびロードできます。

!!! Warning "全カメラ保存時の注意"
    「Save All Cameras」では、カメラの選択はプルダウン内の何番目かという情報で保存されることに注意してください。 PCからカメラを取り外すと、プルダウン内のカメラの順序が変わり、カメラを正しくロードできなくなります。
