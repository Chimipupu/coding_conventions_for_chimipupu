
# C言語 コーディング規約 (for Chimipupu)

## 改版履歴

- 初版 `CCC-C-REV0`  (2026/03/28)

## 適応範囲

- C言語による組み込み開発
  - 環境: マイコン、Windows、Linux問わず

## 型

- 型は `stdint.h` の型を使用する

```c
// BAD, 悪い例
char hoge;
short foo;
int var;
```

```c
// Good, 良い例
#include <stdint.h>
uint8_t   val_u8;
uint16_t  val_u16;
uin32_t   val_u32;

```

## 命名規則

### 変数命名規則

- Static変数は `s_val` のように頭に `s_` を付けること

- Global変数は `g_val` のように頭に `g_` を付けること

- boolの変数は `is_flg` のように `is_` を付けること

- ポインタ変数は `p_buf` のように `p_` を付けること

### 関数命名規則

- staticの関数は `_func()` のように、関数名の前に `_` を付けること

## 禁止事項

- `goto` は一切の使用を禁止する

- `三項演算子`は一切の使用を禁止する

- `malloc()`は一切の使用を禁止し、固定長のバッファを使用すること

- Arduino環境の`delay()`、Windowsの`sleep()`など、全ての処理をブロッキングして一定時間待つ処理は一切の使用を禁止する

- 関数の中での変数宣言は関数の冒頭のみとし、処理の途中で型の宣言は禁止する

## 開発環境別

- マイコン固有の関数は `_mcu_wrap_func()` のように `_mcu_wrap_` と付くラッパー経由で関数を呼び出すこと

- Windows環境固有の関数は `_win_wrap_func()` のように `_win_wrap_` と付くラッパー経由で関数を呼び出すこと

- Linux環境固有の関数は `_linux_wrap_func()` のように `_linux_wrap_` と付くラッパー経由で関数を呼び出すこと
