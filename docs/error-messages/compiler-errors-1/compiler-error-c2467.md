---
title: コンパイラ エラー C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: aa45cbb19519dea7bd5c8fb96abd2c76ea30a786
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302086"
---
# <a name="compiler-error-c2467"></a>コンパイラ エラー C2467

匿名 'ユーザー定義型' の無効な宣言

入れ子にされたユーザー定義の型が宣言されました。 これは、ANSI 互換オプションを使用する C ソース コードをコンパイルするときのエラー ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) を有効にします。

次の例では、C2467 が生成されます。

```
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```