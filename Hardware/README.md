# ProjectNorthStar 1-10 custom: hardware

## はじめに / Introduction
このフォルダには下記のファイルが含まれています

This folder contains following data
- ProjectNorthStar_1-10_custom: CADデータ / CAD data
- ProjectNorthStar_1-10_custom_BOM.xlsx: 部品表 / Parts list

![](/Hardware/imgs/ProjectNorthStar_1-10_custom.png_drawing.png)

## 組み立て手順 / Assembly instruction
近日公開 / Will be updated soon...


## ハードウェア注意点 / Some notes about the hardware
- ディスプレイのドライブ基板は、信号伝達性が良くないスリムケーブルなどを使用している場合、画面上に白色部分が多くなるとシャットダウンすることがある
  
  When the HDMI cable to the display driver is too 'slim' (thus might cause signal degradation in long span), it may cause white out of the display, or even power failure and shutdown of the driver circuit.

- ディスプレイのフレキシブル基板は、屈曲に弱く切れやすいため組立時に注意すること
  
  The flexible print circuit to the display module is susceptive against bending and easy to cause breakage. Be causcious on assembly.

- Leap Motionのケーブルは切れやすいため、可能なら別途USB3.0 microBケーブルを使用したほうが良い
  
  The original USB cable from LeapMotion is not mechanically well built, get a high-quaility USB3.0 micro cable if possible. 

- リフレクターは、SLAなどの3Dプリンター製のものは真空蒸着をした際に変形することがあるため、PMMA切削加工品を推奨
  
  The reflectors (some folks call lens)  produced by 3D printers like SLA may cause slight deformation during mirror-coating process. We recommend milling PMMA(Acryl) material instead.
