---
title: コンパイラ エラー C3912
ms.date: 11/04/2016
f1_keywords:
- C3912
helpviewer_keywords:
- C3912
ms.assetid: 674e050c-11fb-4db1-8bdf-a3e95b41161d
ms.openlocfilehash: bd66196c35715304577b8f6785261be8bdcdafec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406679"
---
# <a name="compiler-error-c3912"></a>コンパイラ エラー C3912

'event': イベントの種類はデリゲート型である必要があります

イベントは、宣言されましたが、適切な型ではありませんでした。

詳細については、次を参照してください。[イベント](../../extensions/event-cpp-component-extensions.md)します。

次の例では、C3912 が生成されます。

```
// C3912.cpp
// compile with: /clr
delegate void H();
ref class X {
   event int Ev;   // C3912
   event H^ Ev2;   // OK
};
```