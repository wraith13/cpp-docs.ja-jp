---
title: コンパイラ エラー C2977
ms.date: 11/04/2016
f1_keywords:
- C2977
helpviewer_keywords:
- C2977
ms.assetid: 3c4218e0-5d03-4a2b-b757-c507c35f3542
ms.openlocfilehash: c9f2971c60b2d1bbc703696467040c3b1d2e2756
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395340"
---
# <a name="compiler-error-c2977"></a>コンパイラ エラー C2977

'identifier': 型引数が多すぎます

ジェネリックまたはテンプレートの実引数が多すぎます。 ジェネリックまたはテンプレート宣言を確認して、正しい数のパラメーターを調べてください。

次の例では C2977 が生成されます。

```
// C2977.cpp
// compile with: /c
template<class T, int i>
class MyClass {};

template MyClass< int , 1, 1 >;   // C2977
template MyClass< int , 1 >;   // OK
```

C2977 は、ジェネリックを使用しているときも発生する場合があります。

```
// C2977b.cpp
// compile with: /clr
// C2977 expected
generic <class T, class U>
void f(){}

generic <class T>
ref struct GC1 {};

int main() {
   // Delete the following 2 lines to resolve.
   GC1<int, char> ^ pgc1;
   f<int,int,int>();

   // OK
   GC1<int> ^ pgc1;
   f<int, int>();
}
```