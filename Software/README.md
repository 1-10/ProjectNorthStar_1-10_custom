# ProjectNorthStar 1-10 custom: software


## 必要ソフト / Reqired softwares
- Unity [(2018.~)](https://unity3d.com/jp/get-unity/download/archive)
  - プロジェクト動作確認(Unity2018.2.15fで作成)
    
    To run and checking out the project (built on Unity2018.2.15f)
    
- Leapコンポーネント / Leap components
  - [LeapSDK](https://www.leapmotion.com/ja/)
- [Project North Star](https://github.com/leapmotion/ProjectNorthStar/tree/master/Software)プロジェクトファイル / Project file
- [NorthAttach_110.unitypackage](https://github.com/1−10/ProjectNorthStar_1-10_custom/tree/master/Software)

## セットアップ / Set up
### 接続 / Hook up
 画面拡張で右側に接続したディスプレイを配置（接続でデフォルト位置）
 
 Connect the NorthStar and place the extend display to the right (default) 

![](/Software/imgs/display_setting.png)

### プロジェクト設定 / Project setting
1. Unity2018.~にて適当なシーンを作成

   Make a scene on Unity 2018- ![](/Software/imgs/create_project.png)

2. [Project North StarのGitHubレポジトリ](https://github.com/leapmotion/ProjectNorthStar/tree/master/Software)の、ProjectNorthstar/Software以下のUnityPackageをインポート
   
   Goto the [Github repository of the Project North Star](https://github.com/leapmotion/ProjectNorthStar/tree/master/Software), import the UnityPackage in the following folder: *ProjectNorthstar/Software* ![](/Software/imgs/import_package01.png)![](/Software/imgs/import_package02.png)
3. [Project North StarのGitHubレポジトリ](https://github.com/leapmotion/ProjectNorthStar/tree/master/Software)から、LeapMotion/North Star/Scenes/NorthStar.unityシーンを開く
   
   Open the unity scene *LeapMotion/North Star/Scenes/NorthStar.unity* from the [GitHub repository of the Project North Star](https://github.com/leapmotion/ProjectNorthStar/tree/master/Software)![](/Software/imgs/scense_NorthStar.png)

4. R Camera RigのWindow Offset ManagerのxshiftにPC側の幅の値を設定する
   
   Set the 'xshift value' under the 'Window Offset Manager - R Camera Rig' to the window width of the PC side ![](/Software/imgs/R_Camera_Rig_Window_Offset_Manager.png)

5. [NorthAttach_110.unitypacckage](https://github.com/1−10/ProjectNorthStar_1-10_custom/tree/master/Software)を追加でインポートする
   
   Add [NorthAttach_110.unitypacckage](https://github.com/1−10/ProjectNorthStar_1-10_custom/tree/master/Software) to the project
   
   ![](/Software/imgs/import_Attach_110.png)[](/Software/imgs/import_Attach_110.png)

6. Game Viewを表示する
   
   Click 'Move Game View to Headset' button. 
   
   ![](/Software/imgs/Game_View.png)

   North側の画面
   
   It will be looking like this in the NorthStar! Huuray!
   ![Hello My Hand](/Software/imgs/Hello_My_Hand.png)




## キャリブレーション / Calibration
1. キャリブレーションファイル設定
    
    Writing calibration file
    - Serialized Calibrationスクリプトでjsonファイルを設定する
       Set a json file with 'Serialized Calibration (Script)'
        - Calibration Folder： Asset/StreamingAsset
        - Output Calibration File: 任意のjsonファイルを設定 / Locate your own json file
        - Input Calibration File: 任意のjsonファイルを設定 / Locate your own json file
![](/Software/imgs/json_settings.png)

2. アスペクト比を設定 / Set aspect ratio
    - Left/RightScreenのScaleを 1.3, 1.3, 1 に設定する
    
      Set the scale of Left/RightScreen to 1.3, 1.3, 1. ![](/Software/imgs/Left-RightScreen_Scale.png)

3. IPD調整 / Adjust IPD
    - キー操作で目の位置、距離を調整をする
      
      Adjust the position and distance of the eyes with hotkeys ![](/Software/imgs/IPD.png)

4. CalibrationDeformer
    - 左右の映像のズレを調整する
       
      Calibrate deformation of the left and right view
    
    - LeftEye/RightEyeのCalibration Deformerの数値を変更
      
      Adjust values of LeftEye/RightEye ![](/Software/imgs/LeftEye-RightEye_Calibration_Deformer.png)

5. 手のトラッキング位置 / Hand tracking position
    - Leap XR Providerの位置を調整し、手とLeap Motionのボーン表示をあわせる
    
      Adjust the position of Leap XR Provider to match actual hands and Leap Motion's bones
![](/Software/imgs/adjust_tracking.png)

>参考 / Reference [STYLY Developer’s](http://psychic-vr-lab.com/blog/unity/project-north-star-%E3%82%AD%E3%83%A3%E3%83%AA%E3%83%96%E3%83%AC%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E6%96%B9%E6%B3%95/)



## 最適化 / Optimization
キャリブレーション終了後、Ray計算は必要ないので、L,R EyeCameraのAR RayTracerを切る

The AR RayTracer of L,R EyeCamera can be turned off since it won't be necessory after the calibration.

その代わりキャリブレーションが出来なくなるので注意

Please note that you can't do calibration again

これで240FPSまで出せる(ディスプレイ基板は90FPSなので十分)

By now you can reach 240 FPS. (This is sufficient, since the display module's refresh rate is only 90 FPS.)

![](/Software/imgs/AR_RayTracer.png)

Leapを長時間稼働していると輝度補正で手が出てこなくなることがある。

Operating the LeapMotion for long period of time may cause a malfunction, inwhich your hands won't be displayed on adjusting brightness.

その時はロバストモードを切ると改善されることが多い

This behavior can be often solved by turning off the Robust-mode

タスクバーからleapの設定を開いてLeapコントロールパネルを開き、切る

From the Task bar, open the LeapMotion setting control panel, turn the Robust mode off. 

![](/Software/imgs/robust.png)

それでも治らない場合タスクマネージャからLeapサービス再起動

If it doesn't solve the problem, restart LeapMotion service. 

![](/Software/imgs/task_manager.png)
