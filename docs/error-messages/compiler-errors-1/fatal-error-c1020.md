---
title: 致命的なエラー C1020
ms.date: 11/04/2016
f1_keywords:
- C1020
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
ms.openlocfilehash: bdd7a6c87b0e00bd7bef174b8daf0e16cc488a5d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383153"
---
# <a name="fatal-error-c1020"></a>致命的なエラー C1020

予期しない #endif です。

`#endif` ディレクティブに対応する `#if`、 `#ifdef`、または `#ifndef` のディレクティブがありません。 各 `#endif` には対応するディレクティブを指定してください。

次の例では C1020 が生成されます。

```
// C1020.cpp
#endif     // C1020
```

考えられる解決方法:

```
// C1020b.cpp
// compile with: /c
#if 1
#endif
```