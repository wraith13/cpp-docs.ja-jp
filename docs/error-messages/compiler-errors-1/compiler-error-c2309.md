---
title: コンパイラ エラー C2309
ms.date: 11/04/2016
f1_keywords:
- C2309
helpviewer_keywords:
- C2309
ms.assetid: 6303d5b5-72cf-42b8-92ce-b1eb48e80d48
ms.openlocfilehash: 9d114565b6b119711aaa773d76658cc27838f4a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303543"
---
# <a name="compiler-error-c2309"></a>コンパイラ エラー C2309

catch ハンドラーには、かっこで囲まれた例外宣言が必要です。

Catch ハンドラーには、かっこで囲まれた型がありません。

次の例では、C2309 が生成されます。

```
// C2309.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch C {}   // C2309
   // try the following line instead
   // catch( C ) {}
}
```