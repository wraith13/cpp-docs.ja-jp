---
title: コンパイラ エラー C3420
ms.date: 11/04/2016
f1_keywords:
- C3420
helpviewer_keywords:
- C3420
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
ms.openlocfilehash: 3db109598ce0741ca34a230d8925994543bcb5ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182458"
---
# <a name="compiler-error-c3420"></a>コンパイラ エラー C3420

'finalizer' : ファイナライザーを仮想にすることはできません

ファイナライザーは、それを囲む型から非仮想的にのみ呼び出すことができます。 したがって、仮想のファイナライザーを宣言すると、エラーになります。

詳細については、次を参照してください。[する方法のデストラクターおよびファイナライザー。クラスと構造体定義および使用 (C +/cli CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)します。

## <a name="example"></a>例

次の例では C3420 が生成されます。

```
// C3420.cpp
// compile with: /clr /c
ref class R {
   virtual !R() {}   // C3420
};
```