---
title: コンパイラ エラー C3902
ms.date: 11/04/2016
f1_keywords:
- C3902
helpviewer_keywords:
- C3902
ms.assetid: feb3bb29-f836-4d77-ba71-3876f7f4f216
ms.openlocfilehash: d90bf299c566ce72e3d1cbfeb545def0a43d6cbf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375991"
---
# <a name="compiler-error-c3902"></a>コンパイラ エラー C3902

'accessor': 最後のパラメーターの型は 'type' でなければなりません

少なくとも 1 つの set メソッドの最後のパラメーターの型は、プロパティの型と一致する必要があります。 詳細については、「 [property](../../extensions/property-cpp-component-extensions.md)」を参照してください。

次の例では、C3902 が生成されます。

```
// C3902.cpp
// compile with: /clr /c
using namespace System;
ref class X {
   property String ^Name {
      void set(int);   // C3902
      // try the following line instead
      // void set(String^){}
   }

   property double values[int,int] {
      void set(int, int, float);   // C3902
      // try the following line instead
      // void set(int, int, double){}
   }
};
```