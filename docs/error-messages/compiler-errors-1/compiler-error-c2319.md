---
title: コンパイラ エラー C2319
ms.date: 11/04/2016
f1_keywords:
- C2319
helpviewer_keywords:
- C2319
ms.assetid: 25263e6e-f5ba-4d2c-8727-8c2d8ca2e5ce
ms.openlocfilehash: f0ec35cfb74fd08180969344180ff42d485d58c0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404300"
---
# <a name="compiler-error-c2319"></a>コンパイラ エラー C2319

'try/catch' の後に複合ステートメントを指定する必要があります。 '{' が必要です

`try` または `catch` ステートメントの後に `try` または `catch` ブロックが見つかりません。 ブロックは中かっこで囲む必要があります。

次の例では C2319 が生成されます。

```
// C2319.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch( C ) ;    // C2319
   // try the following line instead
   // catch( C ) {}
}
```