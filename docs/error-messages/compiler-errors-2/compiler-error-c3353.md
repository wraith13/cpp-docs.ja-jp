---
title: コンパイラ エラー C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: c38642d7abd4f2fd50792c548c9a5521b2da10ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402646"
---
# <a name="compiler-error-c3353"></a>コンパイラ エラー C3353

'delegate': デリゲートはマネージド型または WinRT 型のグローバル関数またはメンバー関数からのみ作成できます

使用して、デリゲート宣言、[委任](../../extensions/delegate-cpp-component-extensions.md)キーワードは、グローバル スコープでのみ宣言できます。

次の例では C3353 が生成されます。

```
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```