---
title: コンパイラ エラー C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: 788f03e4364404ad5c30b7edcba8b743c7f201ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152424"
---
# <a name="compiler-error-c3846"></a>コンパイラ エラー C3846

'symbol': 'assembly2' からシンボルをインポートできません: 'symbol' は、別のアセンブリ 'assembly1' から既にインポートされていますが、

以前に参照されたアセンブリからインポートされたために、参照されたアセンブリからシンボルをインポートできませんでした。

## <a name="example"></a>例

次の例では、C3846 が生成されます。

```
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

これをコンパイルします。

```
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
