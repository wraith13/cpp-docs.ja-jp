---
title: コンパイラ エラー C2657
ms.date: 11/04/2016
f1_keywords:
- C2657
helpviewer_keywords:
- C2657
ms.assetid: f7cf29a9-684a-4605-9469-ecfee9ba4b03
ms.openlocfilehash: 4e2816092b3c0c210ae2c544e9bf9a823a9c5d18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360438"
---
# <a name="compiler-error-c2657"></a>コンパイラ エラー C2657

' クラス:: *' のステートメントの先頭にある (を忘れました型を指定するか)。

メンバーへのポインターの識別子を持つ行が開始しました。

このエラーは、メンバーへポインターの宣言で型指定子がありませんが発生することができます。

次の例では、C2657 が生成されます。

```
// C2657.cpp
class C {};
int main() {
   C::* pmc1;        // C2657
   int C::* pmc2;   // OK
}
```