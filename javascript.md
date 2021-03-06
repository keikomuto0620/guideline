#JavaScript コーディングガイドライン

##項目

  1. [グローバル変数を使用しない](#グローバル変数を使用しない)
  1. [インデントはタブで4文字分](#インデントはタブで4文字分)
  1. [変数名はローワーキャメル形式で宣言](#変数名はローワーキャメル形式で宣言)
  1. [数字や文字列の比較では厳密等価演算子を使う](#数字や文字列の比較では厳密等価演算子を使う)
  1. [for文で、配列をループさせる場合は最初に配列の長さを変数に格納しておく](#for文で、配列を使う場合は最初に配列の長さを変数に格納しておく)
  1. [オブジェクトの指定方法](#オブジェクトの指定方法)
  1. [プロパティの削除にdeleteは使わない](#プロパティの削除にdeleteは使わない)
  1. [jQuery](#jQuery)

##グローバル変数を使用しない

変数同士が衝突して思わぬバグにつながる可能性があるから。
変数を宣言する時は必ず```var```をつけてください。

##なるべく無名関数でソースを括る

例

```javascript
(function(){
	//処理
})(jQuery);

```

##インデントはタブで4文字分
CSSやHTMLのコーディングルールとあわせて統一性を持たせる

##変数名はローワーキャメル形式で宣言
CSSやHTMLのコーディングルールとあわせて統一性をもたせる

例

```javascript
var isActive = false;
```

##数字や文字列の比較では厳密等価演算子を使う
厳密等価演算子の方が等価演算子

例
```javascript
if(string === "hoge"){
	//処理
}
```
##for文で、配列を使う場合は最初に配列の長さを変数に格納しておく
arrayのlengthプロパティに何回もアクセスすると処理速度に影響が出るため

悪い例
```javascript
for(var i = 0; i < array.length; i++){
	//処理
}
```
良い例
```javascript
for(var i = 0, length = array.length; i < length; i++){
	//処理
}
```

##オブジェクトの指定方法
1. オブジェクトの指定は見やすいように下の「良い例」のように記述するようにしましょう

良い例
```javascript
var map = {
	hoge: "hogehoge",
	test: "testtest"
}
```

悪い例
```javascript
var map = {hoge: "hogehoge",
test: "testtest"}

2. オブジェクトの生成では```new Object()```を使わないようにしましょう
{}で生成する方が、記述がシンプルで、かつ実行速度が速いです。

良い例
```javascript
var obj = {};
```

悪い例
```javascript
var obj = new Object();
```

##プロパティの削除にdeleteは使わない
プロパティの削除より、nullを代入する方が処理が速いため

良い例
```javascript
obj.hoge = null;
```

悪い例

```javascript
delete obj.hoge
```

##jQuery

###プロトタイプチェーンをなるべくつなげる

要素を既に取得済みのため処理が早くなるから

例

```javascript
$(".hoge").addClass("active")
		.removeClass("disable")
		.hide();
```

###複数回要素を使用する場合は最初に変数にデータを格納しておく
$(セレクタ)の処理に時間がかかるため

例

```javascript
var $hoge = $(".hoge");
$hoge.func();
/*処理*/
$hoge.func();
```

