# ProjectNorthStar 1-10 custom: software


## 必要ソフト
- Unity [(2018.~)](https://unity3d.com/jp/get-unity/download/archive)
  - プロジェクト動作確認(Unity2018.2.15fで作成)
- Leapコンポーネント
  - [LeapSDK](https://www.leapmotion.com/ja/)
- [Project North Star](https://github.com/leapmotion/ProjectNorthStar/tree/master/Software)プロジェクトファイル
- [NorthAttach_110.unitypackage](https://github.com/1−10/ProjectNorthStar_1-10_custom/tree/master/Software)

## セットアップ
### 接続
 画面拡張で右側に接続したディスプレイを配置（接続でデフォルト位置） ![](/Software/imgs/display_setting.png)

create_project.png
### プロジェクト設定
1. Unity2018.~にて適当なシーンを作成![](/Software/imgs/create_project.png)

2. [Project North StarのGitHubレポジトリ](https://github.com/leapmotion/ProjectNorthStar/tree/master/Software)の、ProjectNorthstar/Softwar以下のUnityPacageをインポート![](/Software/imgs/import_package01.png)![](/Software/imgs/import_package02.png)

3. [Project North StarのGitHubレポジトリ](https://github.com/leapmotion/ProjectNorthStar/tree/master/Software)から、LeapMotion/North Star/Scenes/NorthStar.unityシーンを開く![](/Software/imgs/scense_NorthStar.png)

4. R Camera RigのWindow Offset ManagerのxshiftにPC側の幅の値を設定する![](/Software/imgs/R_Camera_Rig_Window_Offset_Manager.png)

5. [NorthAttach_110.unitypacckage](https://github.com/1−10/ProjectNorthStar_1-10_custom/tree/master/Software)を追加でインポートする![](/Software/imgs/import_Attach_110.png)

6. Game Viewを表示する ![](/Software/imgs/Game_View.png)

     North側の画面 ![Hello My Hand](/Software/imgs/Hello_My_Hand.png)




## キャリブレーション
1. キャリブレーションファイル設定
    - Serialized Calibrationスクリプトでjsonファイルを設定する
        - Calibration Folder： Asset/StreamingAsset
        - Output Calibration File: 任意のjsonファイルを設定
        - Input Calibration File: 任意のjsonファイルを設定
        ![](/Software/imgs/json_settings.png)

2. アスペクト比を設定
    - Left/RightScreenのScaleを 1.3, 1.3, 1 に設定する ![](/Software/imgs/Left-RightScreen_Scale.png)

3. IPD調整
    - キー操作で目の位置、距離を調整をする ![](/Software/imgs/IPD.png)

4. CalibrationDeformer
    - 左右の映像のズレを調整する
    - LeftEye/RightEyeのCalibration Deformerの数値を変更 ![](/Software/imgs/LeftEye-RightEye_Calibration_Deformer.png)
5. 手のトラッキング位置
    - Leap XR Providerの位置を調整し、手とLeap Motionのボーン表示をあわせる ![](/Software/imgs/adjust_tracking.png)

>参考[STYLY Developer’s](http://psychic-vr-lab.com/blog/unity/project-north-star-%E3%82%AD%E3%83%A3%E3%83%AA%E3%83%96%E3%83%AC%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E6%96%B9%E6%B3%95/)



## 最適化
キャリブレーション終了後、Ray計算は必要ないので、L,REyeCameraのAR RayTracerを切る
その代わりキャリブレーションが出来なくなるので注意
これで240FPSまで出せる(ディスプレイ基板は90FPSなので十分)
![](/Software/imgs/AR_RayTracer.png)

Leap長時間稼働していると輝度補正で手が出てこなくなることがある。
その時はロバストモードを切ると改善されることが多い
タスクバーからleapの設定を開いてLeapコントロールパネルを開き、切る
![](/Software/imgs/robust.png)

それでも治らない場合タスクマネージャからLeapサービス再起動
![](/Software/imgs/task_manager.png)
