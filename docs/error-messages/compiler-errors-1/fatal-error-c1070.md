---
title: 致命的なエラー C1070
ms.date: 11/04/2016
f1_keywords:
- C1070
helpviewer_keywords:
- C1070
ms.assetid: 1058269a-5db6-4c23-a97f-b5269eb9188b
ms.openlocfilehash: 7e156a230ce9550b65d1b8775947fc7294c15377
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166920"
---
# <a name="fatal-error-c1070"></a>致命的なエラー C1070

ファイル 'filename' 中で #if と #endif が対応していません

`#if`、 `#ifdef`、 `#ifndef` のいずれかのディレクティブには、対応する `#endif`がありません。

次の例では C1070 が生成されます。

```
// C1070.cpp
#define TEST

#ifdef TEST

#ifdef TEST
#endif
// C1070
```

考えられる解決策:

```
// C1070b.cpp
// compile with: /c
#define TEST

#ifdef TEST
#endif

#ifdef TEST
#endif
```