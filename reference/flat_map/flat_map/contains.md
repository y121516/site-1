# contains
* flat_map[meta header]
* std[meta namespace]
* flat_map[meta class]
* function[meta id-type]
* cpp23[meta cpp]

```cpp
bool contains(const key_type& x) const; // (1) C++23

template <class K>
bool contains(const K& x) const;        // (2) C++23
```


## 概要
指定されたキー`x`に一致する要素がコンテナに含まれているかを判定する。

- (1) : クラスのテンプレートパラメータ`key_type`型のキーを受け取る
- (2) : `key_type`と比較可能な`K`型のキーを受け取る


## 戻り値
以下と等価：

```cpp
return find(x) != end();
```
* find[link find.md]
* end()[link end.md.nolink]


## 計算量
対数時間


## 例
```cpp example
#include <iostream>
#include <flat_map>

int main()
{
  std::flat_map<char, int> m = {
    {'a', 3},
    {'b', 1},
    {'c', 4}
  };

  // キー'b'の要素が含まれているか
  if (m.contains('b')) {
    std::cout << "contain" << std::endl;
  }
  else {
    std::cout << "doesn't contain" << std::endl;
  }
}
```
* contains[color ff0000]

### 出力
```
contain
```


## バージョン
### 言語
- C++23

### 処理系
- [Clang](/implementation.md#clang): ??
- [GCC](/implementation.md#gcc): ??
- [Visual C++](/implementation.md#visual_cpp): ??