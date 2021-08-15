# blenderで作った３DモデルをWebに表示

![result](https://user-images.githubusercontent.com/16290220/129480760-f0fde325-7222-4b4e-9e0c-0f1fcdf58324.gif)

## DEMO
https://yuki-sakaguchi.github.io/threejs-blender/

## blenderで作ったモデルをエクスポート
Webで使えるようにエクスポートする。  
`glTF`でエクスポートすればOK。  
  
エクスポートした時に書き出されるファイルが3つ。  

- .glTF（JSON形式の3Dファイルフォーマット）
- .bin（頂点データ）
- .png（テクスチャ）

これらをhtmlと同じディレクトリに置いて参照する。  
実際にthree.jsで読み込むのはglTFファイルだけ。  
そうすると同じディレクトリ内にある.bin, .pngを読み込むようになってる。

## GLTFLoader.jsを使って読み込む
three.jsの基礎は飛ばす。  
glTFファイルを読み込むために`GLTFLoader.js`も一緒に読み込んでおく。  

以下のように読み込みが完了したらシーンに追加することで表示される。
```
const loader = new THREE.GLTFLoader();

loader.load('cake.gltf', (data) => {
  const gltf = data;
  const object = gltf.scene;
  scene.add(object);
});
```

## 参考
- BlenderでFBX形式をglTF形式に変換してThree.jsでアニメーションさせる
  - https://ryo620.org/2018/02/to-gltf-from-fbx-by-blender/
