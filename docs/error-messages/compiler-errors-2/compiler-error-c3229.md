---
title: コンパイラ エラー C3229
ms.date: 11/04/2016
f1_keywords:
- C3229
helpviewer_keywords:
- C3229
ms.assetid: f2d90923-aa8b-444f-ab10-1f37dbb864e1
ms.openlocfilehash: a3716bafd92bbcd5875ab2ba317f0c6826289c59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62173874"
---
# <a name="compiler-error-c3229"></a>コンパイラ エラー C3229

'type': ジェネリック型パラメーターで間接指定することはできません

ジェネリック パラメーターを `*`、 `^`、または `&`とともに使用することはできません。

## <a name="example"></a>例

次の例では C3229 が生成されます。

```
// C3229.cpp
// compile with: /clr /c
generic <class T>
ref class C {
   T^ t;   // C3229
};

// OK
generic <class T>
ref class D {
   T u;
};
```

## <a name="example"></a>例

次の例では C3229 が生成されます。

```
// C3229_b.cpp
// compile with: /clr /c
generic <class T>   // OK
ref class Utils {
   static void sort(T elems[], size_t size);   // C3229
   static void sort2(T elems, size_t size);   // OK
};
```