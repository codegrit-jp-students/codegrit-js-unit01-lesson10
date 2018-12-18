## オブジェクトのスプレッド演算子 ...

上記の配列でもスプレッド演算子について学びました。
ここではオブジェクトでスプレッド演算子を表記する例を見ていきましょう。

```javascript
const arr = { a: 1, b: 2 };

// オブジェクトのクローン
const arrClone = {...arr};
console.log(arrClone); // { a: 1, b: 2 }

// プロパティを追加した新しいオブジェクトの生成
const addNewArr = {...arr, c: 3};
console.log(addNewArr);// { a: 1, b: 2, c: 3 }

// オブジェクトのマージ
const arrMerge = {...arr, ...{c: 3, d: 4}};
console.log(arrMerge);// { a: 1, b: 2, c: 3, d: 4 }

// 元のオブジェクトに同名プロパティがある場合は置き換わる
const foo = {...arr, b: 3};
console.log(foo);// { a: 1, b: 3 }
const yaa = {...arr, ...{a: 3, b: 4}};
console.log(yaa);// { a: 3, b: 4 }
```

`Object.assign()`という書き方をするメソッドのものもありますが、スプレッド演算子で書き換えが可能になります。

## オブジェクトの分割代入

上記のスプレッド演算子を使用することで、配列でもオブジェクトでも**分割代入（Destructing Assignment）**が、簡潔に記述できるようになります。
上記の配列の文化いつ代入でも使った例にオブジェクトの例を加えて、以下の配列とオブジェクトの構文（スプレッド演算子なし）をまずは見ていきましょう。

```js
const arr = [1, 2, 3];
const [a, b, c] = arr;

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3

const obj = {
  foo: 1,
  yaa: 2,
  boo: 3
};
const { foo } = obj;

console.log(foo); // 1
console.log(yaa); // 2
console.log(boo); // 3
```

上記の構文ではスプレッド演算子を用いていません。
そのため、要素を取り出してから、個別にそれぞれの変数`a, b, c`に代入しています。

この構文の方法でも十分便利ではありますが、個別に変数に代入するのは少し重複して書く似た内容が多いですね。
スプレッド演算子を組み合わせることで、配列要素を取り出しながら、その残りを変数に一気に代入することができます。

```js
const arr = [1, 2, 3];
const [d, ...e] = arr;

console.log(d); // 1
console.log(e); // [2, 3]

const obj = {
  foo: 1,
  yaa: 2,
  boo: 3
};
const { foo, ...rest } = obj;

console.log(foo); // 1
console.log(rest); // { yaa: 2, boo: 3 }
```

`...rest`でスプレッド演算子を使用して、一括で残りの配列要素である「2, 3」を変数eやrestに一気に代入しています。

## オブジェクトの更新/書き換え

オブジェクトを初期化するオブジェクト初期化子で、スターウォーズの主人公の一人であるジェダイ、レイのプロフィール情報を初期化によって参照しました。

今度は別のジェダイ、ルークのプロフィールをレイのプロフィールから更新しようと思います。

```js
const obj = {};

const person =  {
  name: "Rey",
  gender: "female",
  info: {
    occupation: "Jedi",
    affiliation: "Resistance",
  }
}

person.name = "Luke";
person.gender = "male";
console.log(person.name, person.gender); // Luke male
```

これで新しく、同じジェダイでもレイではなく、ルークのプロフィールに更新/書き換えされました。

## オブジェクトの削除

今度はオブジェクトを削除してみましょう。
正確にはオブジェクトのプロパティを消すメソッドで、配列でも出てきたdelete演算子を使ってオブジェクトも削除することができます。

上記でレイのプロフィールをルークのプロフィールに書き換えましたが、性別にあたる`gender`を削除してみます。

```js
delete person.gender;
console.log(person); // {name: "Luke", info: {occupation: "Jedi", affiliation: "Resistance"}
```

性別にあたる`gender`の値だけ削除することに成功しました。

## オブジェクトとfor-in文、forEachとObject.keys

オブジェクトと組み合わせて使えるループには以下の種類があります。

```js
// for ... in
let obj = {num1: 1, num2: 2, num3: 3};

for (let v in obj) {
  console.log(obj[v]);
} // 1 2 3

// forEach と Object.keysの組み合わせ
Object.keys(obj).forEach((key) => {
  console.log(key + ':' + obj[key]);
}); // num1:1 num2:2 num3:3
```

for文は上記の配列でも確認しましたが、そのほか、`for ... in`、`forEach`と`Object.keys`の組み合わせについて簡単に復習すると、以下の内容になります。

- `for ... in` - オブジェクトの中身を取得し、その個数分だけ繰り返し処理が可能。ただし、配列の`for ... in`のようにリスクがある。

- `forEach`と`Object.keys`の組み合わせ - Object.keysで配列にしてからforEachしている。forEachは配列に特化した構文。配列データの値1つずつにコールバック関数に記述した処理を実行する。

forEach構文も、`for ... of`と同様に「繰り返し回数」や「カウンタ変数」などを用意する必要なく扱えるため、最近ではよく使われています。

## 更に学ぼう

### 動画で学ぶ

- [JavaScript入門 - ドットインストール](https://dotinstall.com/lessons/basic_javascript_v2)

### 本で学ぶ

- [Eloquent JavaScript 3rd Edition](http://eloquentjavascript.net/)
