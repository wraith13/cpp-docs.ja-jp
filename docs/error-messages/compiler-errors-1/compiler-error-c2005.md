---
title: コンパイラ エラー C2005
ms.date: 11/04/2016
f1_keywords:
- C2005
helpviewer_keywords:
- C2005
ms.assetid: 090530ed-e0ec-4358-833a-ca24260e7ffe
ms.openlocfilehash: 49d0375d5733410d728797d2a881075377b33ba6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209004"
---
# <a name="compiler-error-c2005"></a>コンパイラ エラー C2005

\#line は行番号が必要です。'トークン'が見つかりました。

`#line`ディレクティブの行番号を後にする必要があります。

次の例では、C2005 が生成されます。

```
// C2005.cpp
int main() {
   int i = 0;
   #line i   // C2005
}
```

考えられる解決方法:

```
// C2005b.cpp
int main() {
   int i = 0;
   #line 0
}
```