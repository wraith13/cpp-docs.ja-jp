---
title: コンパイラの警告 (レベル 3) C4635
ms.date: 11/04/2016
f1_keywords:
- C4635
helpviewer_keywords:
- C4635
ms.assetid: b2ba90de-c093-4a76-8076-b65878467574
ms.openlocfilehash: b6fd45dc6c28c0d12eb2b2991f8a087b1841d1a9
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189147"
---
# <a name="compiler-warning-level-3-c4635"></a>コンパイラの警告 (レベル 3) C4635

XML ドキュメント コメント対象: XML の形式が正しくありません: 理由

コンパイラは XML タグに何らかの問題を検出しました。  問題を修正して再コンパイルします

次の例では C4635 が生成されます。

```cpp
// C4635.cpp
// compile with: /doc /clr /W3 /c
/// <summary>
/// The contents of the folder have changed.
/// <summary/>   // C4635

// try the following line instead
// /// </summary>
public ref class Test {};
```

このサンプルの次の出力に注意してください: **'member' の終了タグが開始タグ 'summary' と一致しません。**

このサンプルの問題は、\<summary > の終了タグの形式が適切ではなく、コンパイラが \<の概要 > 終了タグとして認識していないことです。  \<のメンバー > タグは、すべての/doc コンパイルでコンパイラによって .xdc ファイルに埋め込まれます。  ここでの問題は、終了タグ \</メンバー > が、コンパイラが処理した前の開始タグ (\<概要 > と一致しないことです。