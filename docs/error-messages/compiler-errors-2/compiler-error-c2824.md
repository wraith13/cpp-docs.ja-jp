---
title: コンパイラ エラー C2824
ms.date: 11/04/2016
f1_keywords:
- C2824
helpviewer_keywords:
- C2824
ms.assetid: 5bd865f7-e0af-404e-80fe-e2b798b44a59
ms.openlocfilehash: 226fc078312a214c561e80064474ee237245c0f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406939"
---
# <a name="compiler-error-c2824"></a>コンパイラ エラー C2824

型の戻り値の 'operator new' である必要があります ' void *'

演算子のオーバー ロードとベース以外のポインター、`new`返す必要があります`void *`します。

次の例では、C2824 が生成されます。

```
// C2824.cpp
// compile with: /c
class   A {
   A* operator new(size_t i, char *m);   // C2824
   // try the following line instead
   // void* operator new(size_t i, char *m);
};
```