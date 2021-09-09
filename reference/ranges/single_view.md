# single_view
* ranges[meta header]
* std::ranges[meta namespace]
* class template[meta id-type]
* cpp20[meta cpp]

```cpp
namespace std {
  namespace ranges {
    template<copy_constructible T>
    requires is_object_v<T>
    class single_view : public view_interface<single_view<T>> { …… }; // (1)

    namespace views {
      inline constexpr unspecified single = unspecified; // (2)
    }
  }

  namespace views = ranges::views;
}
```
* copy_constructible[link /reference/concepts/copy_constructible.md]
* is_object_v[link /reference/type_traits/is_object.md]
* view_interface[link view_interface.md]

## 概要
`single_view`は、要素1つからなる範囲を表す[`view`](view.md)。

`single_view`のオブジェクトは(2)のカスタマイゼーションポイントオブジェクト`views::single`で生成できる。

### 範囲カテゴリ

| borrowed | sized | output | input | forward | bidirectional | random_access | contiguous | common | viewable | view |
|----------|-------|--------|-------|---------|---------------|---------------|------------|--------|----------|------|
|          | ○    | ○     | ○    | ○      | ○            | ○            | ○         | ○     | ○       | ○   |

## テンプレートパラメータ制約
[`is_object_v`](/reference/type_traits/is_object.md)`<T>`

## 効果
- 式`views::single(E)`の効果は`single_view{E}`と等しい。

## メンバ関数

| 名前                                             | 説明                             | 対応バージョン |
|--------------------------------------------------|----------------------------------|----------------|
| [`(constructor)`](single_view/op_constructor.md.nolink)  | コンストラクタ                   | C++20          |
| [`begin`](single_view/begin.md.nolink)                   | 先頭を指すイテレータを取得する   | C++20          |
| [`end`](single_view/end.md.nolink)                       | 番兵を取得する                   | C++20          |
| [`data`](single_view/data.md.nolink)                     | 配列の先頭へのポインタを取得する | C++20          |

## 静的メンバ関数

| 名前                                             | 説明                             | 対応バージョン |
|--------------------------------------------------|----------------------------------|----------------|
| [`size`](single_view/size.md.nolink)                     | 要素数を取得する                 | C++20          |

## 継承しているメンバ関数

| 名前                                         | 説明                             | 対応バージョン |
|----------------------------------------------|----------------------------------|----------------|
| [`operator bool`](view_interface/op_bool.md) | 範囲が空でないかどうかを判定する | C++20          |
| [`front`](view_interface/front.md)           | 先頭要素への参照を取得する       | C++20          |
| [`back`](view_interface/back.md)             | 末尾要素への参照を取得する       | C++20          |
| [`operator[]`](view_interface/op_at.md)      | 要素へアクセスする               | C++20          |

## 例
```cpp example
#include <ranges>
#include <iostream>

int main() {
  using namespace std;

  for(int n : views::single(1)) {
    cout << n;
  }
}
```
* views::single[color ff0000]

### 出力
```
1
```

## バージョン
### 言語
- C++20

### 処理系
- [Clang](/implementation.md#clang): 13.0.0
- [GCC](/implementation.md#gcc): 10.1.0
- [ICC](/implementation.md#icc): ?
- [Visual C++](/implementation.md#visual_cpp): 2019 Update 10

## 参照
- [N4861 24 Ranges library](https://timsong-cpp.github.io/cppwp/n4861/ranges)
- [C++20 ranges](https://techbookfest.org/product/5134506308665344)