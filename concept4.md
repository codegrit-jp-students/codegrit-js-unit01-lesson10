# オブジェクト（Object）

## オブジェクトとは

オブジェクトについてはレッスン2ですでに詳しく概要を学んでいます。
オブジェクトはいわゆる**入れ物=箱**のようなものであり、入れ物としての箱は変わらず、箱の中身だけが時間や処理の進行に伴って変わっているイメージということを学びました。

ここでは簡単に配列を詳しく学んだので、配列との違いを比較してみます。

**配列**

- 配列には値がある。インデックス番号でアクセスが可能。
- 配列要素には順番がある。

**オブジェクト**
- オブジェクトにはプロパティ（オブジェクトに記載される内容）がある。文字列、もしくはシンボルを使って要素にアクセスが可能。
- オブジェクトのプロパティには順序がない。


ちなみに、**連想配列**というものを専門書や様々なところで見かけることがあるかと思いますが、他のプログラムで言う連想配列とは、JavaScriptではオブジェクトと同じとみなされます。

ただし、JavaScriptのオブジェクトには値としてデータだけでなく、関数処理も入れることができるのが特徴です。
つまり連想配列でも関数が値として入っている場合はオブジェクトと呼びます。

## オブジェクトの値の取り出し

オブジェクトの値を取り出すには、`Object.values()`を使うことで取得できます。
ここで`Object.values()`を使って、映画スターウォーズ/フォースの覚醒の主人公であるジェダイ、レイの名前と出身惑星を取り出してみましょう。

```javascript
const obj = {
  name: 'Rey',
  from: 'Jakku',
};

console.log(Object.values(obj)); // ['Rey', 'Jakku']
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/mc92pxLe/1/embedded/js,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

戻り値として、オブジェクトが所有しているプロパティの値からなる配列、つまりレイの名前と、レイの出身惑星、ジャクーが値として返ってきました。

## オブジェクトの初期化

オブジェクトの初期化には2つ方法があり。**オブジェクト初期化子**と**コンストラクタ関数**を使用する方法です。

名前だけ見ると理解が難しいので、実際に例を先に見てみましょう。
ジェダイであるレイのプロフィールを、オブジェクトの初期化子とコンストラクタ関数を使って紹介してみます。

```javascript
// オブジェクト初期化
const obj = {}; // 空のオブジェクトを作成

// personオブジェクト作成
const person =  {
  name: "Rey",
  gender: "female",
  info: {
    occupation: "Jedi", // ２階層でオブジェクトを入れることも可
    affiliation: "Resistance",
  },
};

console.log(
  person.name,
  person.gender,
  person.info.occupation,
  person.info.affiliation
); // Rey female Jedi Resistance
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/up8wf6ar/3/embedded/js,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>

まず空のオブジェクトを作成した後に、`person`という新たなオブジェクトを作り、初期化を図っています。
レッスン2でも出てきたプロパティにアクセスするためのドット「.」**メンバーアクセス演算子**を使って、レイのプロフィール情報にアクセスしています。

## インスタンス化

次の例のようにコンストラクタ関数を使って新たにオブジェクトを作成することを**インスタンス化**と呼びます。また生成されたオブジェクトのことを**インスタンス**と呼びます。`person`はPersonというコンストラクタ関数のインスタンスと言えます。

```js
// コンストラクタ関数

// 関数を定義
function Person (name, gender, info) {
  this.name = name;
  this.gender = gender;
  this.info = info;
}

// newでインスタンス化
const person = new Person(
  "Rey",
  "female",
  {
    occupation: "Jedi",
    affiliation: "Resistance"
  }
);

console.log(person.name); //　Rey
```

<iframe width="100%" height="300" src="//jsfiddle.net/codegrit_hiro/jb27ec1a/2/embedded/js,result/dark/" allowfullscreen="allowfullscreen" allowpaymentrequest frameborder="0"></iframe>
