---
title: コンパイラ エラー C2659
ms.date: 11/04/2016
f1_keywords:
- C2659
helpviewer_keywords:
- C2659
ms.assetid: b0883600-4d27-4ca7-a931-8ca6bd48654d
ms.openlocfilehash: 1b44ef825626f60e9ae6c6e8600953959fcd7b3a
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449231"
---
# <a name="compiler-error-c2659"></a>コンパイラ エラー C2659

'演算子' : 関数が演算子の左辺にあります

関数が、指定された演算子の左側にあります。 このエラーの最も一般的な原因は、開発者が変数のつもりで提供した演算子の左側にある ID を、コンパイラが関数として解析したことです。 詳細については、Wikipedia を参照してください。 記事[最も厄介な解析](https://en.wikipedia.org/wiki/Most_vexing_parse)します。 この例は、混乱しやすい関数宣言と変数定義を示しています。

```
// C2659a.cpp
// Compile using: cl /W4 /EHsc C2659a.cpp
#include <string>
using namespace std;

int main()
{
   string string1(); // string1 is a function returning string
   string string2{}; // string2 is a string initialized to empty

   string1 = "String 1"; // C2659
   string2 = "String 2";
}
```

この問題を解決するには、ID の宣言を変更して、その宣言が関数宣言として解析されないようにします。

C2659 エラーは、指定した演算子の左側にある関数の型を式で使用できない場合にも発生する可能性があります。 この例では、コードが関数ポインターを関数に割り当てるときに C2659 が生成されます。

```
// C2659b.cpp
// Compile using: cl /W4 /EHsc C2659b.cpp
int func0(void) { return 42; }
int (*func1)(void);

int main()
{
   func1 = func0;
   func0 = func1; // C2659
}
```