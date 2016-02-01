# raspiでArduinoとシリアル通信 on Nodejs

## Step1: 準備
raspiとArduinoのシリアル通信をnodejs上で利用するにはUSBシリアル通信を行う。
そのモジュールが**node-serialport**だ。

>sudo npm install serialport


後で使うArduinoのデバイス名（ポート名）を取得しておく

>dmsg

そこでそれっぽいものを探す
```
1073.352165] usb 1-1.2: new full-speed USB device number 5 using dwc_otg
[ 1073.466606] usb 1-1.2: New USB device found, idVendor=2341, idProduct=0001
[ 1073.466634] usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=220
[ 1073.466651] usb 1-1.2: Product: Arduino Uno
[ 1073.466668] usb 1-1.2: Manufacturer: Arduino (www.arduino.cc)
[ 1073.466684] usb 1-1.2: SerialNumber: 853323433323513192A1
[ 1073.504493] cdc_acm 1-1.2:1.0: ttyACM0: USB ACM device
[ 1073.505640] usbcore: registered new interface driver cdc_acm
[ 1073.505660] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
```
自分の場合は下のほうにArduin unoとあってそのあとに**ttyACM0**というのが見つかる。この**ttyなんちゃら**がデバイスになる。
あとで使うのでメモっておく。

## Step2: 通信する
ここからは前提知識としてnode.js,expressを使うのでそれらが使えること。



## [TOPへ](http://yoshihirox.github.io/)
