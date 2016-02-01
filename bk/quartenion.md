# クォータオンでWebglコンテンツにSketchUp等のようなカメラを実装
## 概要
ライブラリはglMatrix-0.9.5.min.jsを使用<br>
クォータニオンを作成、角度と軸（長さが1のベクトル）を使用し、回転角を作成する。<br>
作成されたクォータニオンをベクトルに適用すればそのベクトルを作成時に指定した軸をベースに回転した座標が得られる。
同様にカメラのupにも適用することによりlookatで指定するカメラの角度が得られる(up)。

quarternionのidentityは[0, 0, 0, 1];

```javascript
var qt = quat4.create([0,0,0,1]);
var rad  =(count % 720) * Math.PI / 360;
quat4.rotate(rad,[1,0,0],qt);
quat4.toVec3([0,0,3],qt,loc);
quat4.toVec3([0,1,0], qt, up);
mat4.lookAt(loc, center, up, matV);
```

.rotateで[1,0,0]軸を中心にradだけ回転したクォータニオンを作成(qt);<br>
qutat4.toVec3(a,q,d)でaベクトルにクォータニオンqを適用したものをdに代入。

しかし、マウス座標は二次元なので2軸に対して回転を適用させる
完全なコードは以下

```javascript
var rad  =(CADCam.center.position[0] ) * Math.PI/10;
var rad2 =(CADCam.center.position[1] ) * Math.PI/10;

var qt = quat4.create([0,0,0,1]);
var qt2 = quat4.create([0,0,0,1]);

quat4.rotate(rad,[0,1,0],qt);
quat4.rotate(rad2,[1,0,0],qt2);

quat4.multiply(qt2,qt);

quat4.toVec3([0,0,3],qt2,loc);
quat4.toVec3([0,1,0], qt2, up);

mat4.lookAt(loc, center, up, matV);
```
x軸の回転とy軸の回転のクォータニオンを作成したらそれらを合成する
`quat4.multiply(qt2,qt);`
