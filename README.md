# nuxt-trello

> My sublime Nuxt.js project

## Build Setup

``` bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```

For detailed explanation on how things work, check out [Nuxt.js docs](https://nuxtjs.org).

# 実装方針

## "Containerコンポーネント" と "Presentational"コンポーネント

* コンポーネントは"Containerコンポーネント"と"Presentationalコンポーネント"に分ける
* 下位コンポーネントはなるべく状態を持たないようにする

### Presentational Component

#### 特徴

1. 見た目に責務を持つ
2. VuexのstoreやVue Routerのrouteなどのアプリケーションの状態に依存せず、他のVueアプリケーションにも流用できる。
3. 必要なデータがどのように読み込まれるか、また、どのように変更されるかを指定しない
4. コンポーネント自身の状態は滅多に持たない。（仮に状態を持つとしても、それはUIに関する状態のみ）
5. 状態を持たせない

Presentational Componentは親からpropsを通して、必要なデータを受け取り、自身を描画するのみ。
本来のPresentational Componentの特徴としては、UIに関する状態であれば、その状態を持っても良いとあります。
仮にVuex側で状態を持たせない方が良い場合は、後述するContainer Component側に持たせます。

#### Functional Component

Leaf Componentと呼ばれるコンポーネントのように、ループ処理の中で同じコンポーネントが描画されるような場合には、Functional ComponentとしてPresentational Componentを実装することも検討。
Functional Componentは単なる関数でインスタンスを持たないため、描画コストを少なく抑えることが可能です。

### Container Component

### 特徴

1. データや振る舞いに責務を持つ
2. データや振る舞いをPresentational Componentや他のContainer Componentに提供する
3. VuexのstoreやVue Routerのrouteを参照しても良い（しなくても良い）
4. 通常、DOMのマークアップやCSSスタイルを持たない。(仮にDOMを持つとしても、それはラッパー用のdivタグなど)

### イベントハンドラーとイベント名の命名規則

* イベントハンドラー名はhandleCancelのようにhandleで始める
* emitするイベント名は、命名規則に沿ったメソッド名からhandleを取り除いた文字列とする

### propsのガイドライン

* 必須のpropsは、requiredをtrue
* 任意のpropsにはdefaultを設定
* データ型を指定
* propsの検証→propsで受け取る値が特定の条件に当てはまる場合は、propsの値にバリデーションを適用

以下はバリデーションの一例

```
props: {
  name: {
    type: String,
    validator (value) {
      return value.length > 0
    }
  },
  count: {
    type: Number,
    validator (value) {
      return value >= 0
    }
  },
  item: {
    type: Object,
    validator (obj) {
      const EXPECTED_KEY = 0
      const EXPECTED_VALUE_TYPE = 1
      const expectedPairs = [
        ['name', 'string'],
        ['count', 'number']
      ]
      const pairs = Object.entries(obj);

      return pairs.every(([KEY, VALUE], index) => {
        return KEY === expectedPairs[index][EXPECTED_KEY] && typeof VALUE === expectedPairs[index][EXPECTED_VALUE_TYPE]
      })
    }
  },
  mode: {
    type: String,
    validator (value) {
      const modes = ['easy', 'difficult']
      return modes.includes(value)
    }       
  },
  selectedIds: {
    type: Array,
    validate (values) {
      return values.every(value => typeof value === 'string')
    }
  },
  date: {
    type: Date,
    validate (value) {
      return value >= new Date(2000, 01, 01)
    }
  }
}
```

### スタイル規則

* Scoped SCSSを使用
* 要素型セレクターは使わない
* ケバブケースのクラス名を&や変数展開で繋がない



### option

* 「パフォーマンスに影響があるなどの特別な理由がない限り、全ての状態をVuexに寄せる」という方針があるため、Presentational Componentが状態を持つことはありません。仮にVuex側で状態を持たせない方が良い場合は、後述するContainer Component側に持たせます。

## 共通の振る舞いを抽出する・その実装のパターンを知る

* いろんなコンポーネントで使われる共通の振る舞いは、その振る舞い自体を抽出
** 実装するパターンはいくつかあるが、メジャーなものとしてはHigher Order ComponentやRender Prop

## 用語

"Presentationalコンポーネント": 名前の通り見た目だけに責務を持ち、自身では状態を持たない


# 参考記事

* [フロントエンドのコンポーネント設計に立ち向かう](https://qiita.com/seya/items/8814e905693f00cdade2)
* [Vueを用いた開発プロジェクト用に「コンポーネント設計・実装ガイドライン」を作った話](https://qiita.com/HayatoKamono/items/72b02d439a83d68fc15a)
* [Vuexを用いた開発プロジェクト用にガイドラインを作成した話](https://qiita.com/HayatoKamono/items/eb6d253a1c73ab001659)
