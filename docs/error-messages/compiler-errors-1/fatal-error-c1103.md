---
title: 致命的なエラー C1103
ms.date: 11/04/2016
f1_keywords:
- C1103
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
ms.openlocfilehash: b6253af9fcf400321fb58d4d8a6d7aacf461b926
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62174201"
---
# <a name="fatal-error-c1103"></a>致命的なエラー C1103

progid をインポート中の致命的なエラー: 'message'

コンパイラがタイプ ライブラリのインポートで問題を検出しました。  たとえば、progid を持つタイプ ライブラリを指定し、さらに `no_registry`を指定することはできません。

詳細については、次を参照してください。 [#import ディレクティブ](../../preprocessor/hash-import-directive-cpp.md)します。

次の例では C1103 エラーが生成されます。

```
// C1103.cpp
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103
```