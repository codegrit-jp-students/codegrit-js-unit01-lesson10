## 配列のメソッド

### 配列の要素の追加

**_pushメソッド_**を使うことで、**配列の最後**に要素を追加することができます。逆に、**_unshiftメソッド_**は**配列の先頭**に要素を追加します。
2つとも戻り値は変更された後の配列の長さを返します。

```js
const arr = ['1', '2', '3'];

console.log(arr.push('4')); // 4(追加された要素を合わせた配列の長さ)
console.log(arr.unshift('0')); // 5(追加された要素を合わせた配列の長さ)
console.log(arr) // ['0', '1', '2', '3', '4']
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/j1hkeytr/1/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

### 配列の要素の削除

**_popメソッド_**を使うことにより、**配列の最後**にある要素を消し、配列そのものを変更することができます。逆に、**_shiftメソッド_**は**配列の先頭**にある要素を削除して、配列そのものを変更します。
**_shiftメソッド_**の戻り値は削除された要素を返します。

```js
let arr = ['1', '2', '3'];

let x = arr.pop();

console.log(x); // '3'
console.log(arr); // ["1", "2"]
console.log(arr.shift()); // '1' (削除された要素)
console.log(arr); // ["2"]
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/pamxow4c/1/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

**_delete演算子_**を使って配列要素を消すこともできます。削除したい配列要素のインデックス以下のように指定することで、指定された要素だけ消すことができます。(消された要素の場所にはundefinedが入ります。)
戻り値が文字列の数字だけでは少しつまらないので、カフェのドリンクメニューを想定して、品切れになったラテ マキアートを**_delete演算子_**を使ってメニューから削除してみましょう。

```js
let drinks = [
  'cappccino',
  'latte machiato',
  'ice mocha',
  'chai tea latte',
  'white mocha',
];

delete drinks[1];

console.log(drinks); // ["cappccino", undefined, "ice mocha", "chai tea latte", "white mocha"]
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/xo50cfra/1/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

この例ではインデックスで数えて1番目の配列要素のラテ・マキアートが削除されて配列要素のメニューから削除されたことが確認できました。

今度は複数の配列要素を削除する方法について見ていきましょう。
上記の例ではどれも1つずつ配列要素を削除していて、削除できるのも配列要素の先頭と一番後ろ、指定されたインデックスの箇所1つだけが削除可能でした。

もし、カフェのメニューで複数のドリンクが材料が足りずに品切れになった場合はどうしたらいいのでしょうか？
上記の方法では1つずつ消していくしか方法はありませんが、**_spliceメソッド_**を使うことで複数の、しかも指定した個数と箇所を自由に削除することが可能になります。
カフェのメニューの上から2番目に書いてあるラテ・マキアートとアイス・モカが品切れなので、メニューから削除し、店長にどのメニューが品切れかを伝えましょう。
インデックス0から数えて１番目にある配列要素から2つ配列要素を消すということですね。

```js
let drinks = [
  'cappccino',
  'latte machiato',
  'ice mocha',
  'chai tea latte',
  'white mocha'
];

//1番目から2個の要素を削除した値を「menuResult」に代入
let tellYourBoss = drinks.splice(1, 2);

console.log(tellYourBoss); // 消された配列要素が返される['latte machiato','ice mocha']

console.log(drinks); // 残った配列要素が返される["cappccino", "chai tea latte", "white mocha"]
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/utwch5L4/1/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

これで無事メニューの上から2番目に書いてあるラテ マキアートとアイス モカを消すことができ、店長にもどのメニューが品切れかを伝えることができました。

### 配列の置き換え

レッスン2でも簡単な置き換えは見てきましたが、先ほどカフェのメニューを品切れドリンクメニューに合わせて臨機応変に複数指定した箇所で消すことができた、**_spliceメソッド_**で置き換えもできる例を見ていきましょう。

品切れとはいえ、メニューが削除されて減ってしまうだけではお客さんの選択肢が狭められてしまいますよね。
品切れのラテマキアートとアイスモカの代わりに、材料が十分にあって用意可能な代用メニューに置き換えてみます。

```js
let drinks = [
  'cappccino',
  'latte machiato',
  'ice mocha',
  'chai tea latte',
  'white mocha'
];

// インデックスで数えて1番目と２番目の要素をラテとアイス ココアに置き換える
drinks.splice(1, 2, 'latte', 'ice coco');
console.log(drinks);// ['cappccino','latte','ice coco','chai tea latte','white mocha']
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/djuz79f3/2/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

これで品切れのラテマキアートとアイスモカの代用メニューとしてラテとアイス ココアにメニューを書き換えることができました。
メソッドのカッコ中にある例えば「`(1, 2, 'latte', 'ice coco')`」は、左から順にJavaScriptでは **第1引数** **第2引数** **第3引数** **第4引数** と呼びます。（読み仮名は「ひきすう」です。）
書籍などでは引数を使って解説してある内容をよく見かけるので、覚えておくと便利です。

### 配列の値の取り出し

これはレッスン2やこのレッスンの冒頭でも少し述べましたが、配列リテラルでは「[]」（ブラケット）を使ってインデックス番号を0から数えた順番で指定することで、特定の配列要素を呼び出すことができます。以下は例です。

```javascript

const arr = [1, 2, 3, 4]

console.log(arr[0]); // 1
console.log(arr[1]); // 2
console.log(arr[arr.length - 1]); // 4
```

配列の順番は0から始まることに気をつけましょう。上記のように、`arr.length`で配列の長さを得てそこから1を引くことで配列の最後の要素にアクセスすることが出来ます。

### 配列要素の検索

**_indexOf()メソッド_**を使うことで、とても簡単にそれぞれの要素のデータを検索することができます。
ただし、この**_indexOf()メソッド_**は検索したい指定をした要素が存在する場合のみ、存在する順番（場所）をインデックス番号で取得することができるようになっています。

```js
const hello = ['hello', 'こんにちは', 'hallo', 'hola'];
const result = hello.indexOf('こんにちは');

console.log(result); // 1
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/t60zq748/1/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

返り値として、インデックスで数えて1番目にある「こんにちは」のインデックス番号が返ってきました。
まず配列の中に「こんにちは」という文字列の要素が存在するかを確認した上での出力結果であることにも注目しましょう。

試しに配列に存在しない要素で検索をしてみます。

```js
const hello = ['hello', 'こんにちは', 'hallo', 'hola'];
const result = hello.indexOf('Bonjour');

console.log(result); // -1
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/dmvfc7eb/1/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

-1が返り値として返ってきました。
これは配列内に存在しない要素の検索結果として返ってくる戻り値です。

では、検索したい配列要素が複数重複して存在していた場合は戻り値はどうなるのでしょうか？

実際にコードと反映を見て見ましょう。

```js
const hello = ['hello', 'こんにちは', 'hallo', 'こんにちは'];
const result = hello.indexOf('こんにちは');

console.log(result); // 1
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/n4beLv1f/1/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

1というインデックスが返されましたが、検索した「こんにちは」という配列要素は2箇所あります。
インデックス番号で言うと1と3にあるので、2つ戻り値が返されるのかと思いきや、はじめにある配列要素のインデックス番号しか戻り値として返ってきません。

多い配列を扱う場合は、レッスン7で学んだ**while文**などの繰り返し処理を使い、すべての重複要素を取得する方が良いとされています。

さて、ここまで削除や置き換えを除いて、ほぼインデックス番号でしか戻り値は返ってこないメソッドばかりです。
インデックス番号ではなく、配列要素自体を戻り値としたい場合はどうしたら良いのでしょうか？

そういった場合には**_findメソッド_**を使うことで解決します。

**_findメソッド_**は、`true`を返す配列要素が見つかるまで、つまり検索をかけたい特定の配列要素が見つかるまで、要素に対して一度ずつ関数を実行し、**trueを返した = 検索結果に当てはまる配列要素自体を戻り値**として返します。

```js
const arr = [10, 20, 30, 40];

const arrDiv = arr.filter(value => {
  return (value % 20 === 0);
});

console.log(arrDiv); // [20, 40] -> 配列の要素が20で割り切れるものだけを配列要素で返す
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/am5v6gx2/2/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

## mapとfilterメソッド

**_map_**は配列データに使うメソッドです。
それぞれの配列要素に**コールバック関数**を実行した結果、新しい配列として返すと言うメソッドです。
具体的には関数の中に実行したい処理内容を書いておくことで、それぞれの配列要素に対して自由に操作することができます。

**_filterメソッド_**は、特定の条件（例：〜以下の数値のみなど）をコールバック関数内に書くことで、その通りに特定条件のデータを取得することができます。
**_map_**と同じで、全ての要素に対して関数をそれぞれ実行しますが、**_filter_**が**_map_**と違う点は、返り値で `true`を返した配列要素にのみ新しい配列データを作ります。

**_map_**はコールバック関数実行対象の配列の数(実行前)と、新たに作成された配列の数(実行後)は変わりません。

**_map_**と**_filter_**の基本構造はそれぞれ以下です。

```js
// mapメソッド
const arr = [配列要素];

arr.map(コールバック関数);

// filterメソッド
const arr = [配列要素];
arr.filter(コールバック関数);
```

説明だけだと**_map_**と**_filter_**の違いを理解するのは少し難しいので、実際に例を見てみましょう。

```js
/*
* map 例
*/
// 配列の「全ての要素」に20を除算した配列を返す

const arr = [10, 20, 30, 40];

const arrDiv = arr.map(value => {
  return value % 20;
});

console.log(arrDiv); // [10, 0, 10, 0] -< 配列要素「全て」に除算すると言う関数内容が実行された計算結果内容で新しい配列が返された
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/3krf6dgw/1/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

```js
/*
* filter 例
*/
// 配列の「除算できる要素のみ」に20を除算した配列を返す

const arr = [10, 20, 30, 40];

const arrDiv = arr.filter(value => {
  return value % 20;
});

console.log(arrDiv);// [10, 30] → 配列要素のうち、「除算できる要素のみ = trueを返す要素のみ戻り値を返す」と言う関数内容が実行され、新しい配列が返された
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/7eso31bx/1/embedded/js,html,css,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

**_map_**が**全ての配列要素**にコールバック関数で指示した条件内容が実行された計算結果を戻り値としているのに対し、**_filter_**ではコールバック関数で指示した**条件内容に当てはまる配列要素のみ**を文字通りフィルターして戻り値を返しています。

当然**_filter_**の実行結果は、コールバック関数の条件内容によって、返ってくる新しい配列の数は、条件に当てはまらないものを弾いた結果であれば関数実行前よりも少ない場合があります。

これは全ての配列要素に対して関数内容を実行する**_map_**との大きな違いです。
上記の具体例で言葉にすると、**_map_**は区別をせず全ての配列要素に割り算をしたのに対し、**_filter_**では**割り切れる配列要素だけを区別 = フィルタリングして結果を返した**という違いになります。
