---
title: コンパイラの警告 (レベル 3) C4637
ms.date: 11/04/2016
f1_keywords:
- C4637
helpviewer_keywords:
- C4637
ms.assetid: 5fd347c1-2de9-408f-9136-1bf1ff273622
ms.openlocfilehash: e712429ad52ccb990f81e1a4d3bd65a525558692
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "74189119"
---
# <a name="compiler-warning-level-3-c4637"></a>コンパイラの警告 (レベル 3) C4637

XML ドキュメントコメントのターゲット: \<> タグを破棄します。  reason

\<の構文に[>](../../build/reference/include-visual-cpp.md)タグが正しくありませんでした。

次の例では C4637 警告が生成されます。

```cpp
// C4637.cpp
// compile with: /clr /doc /LD /W3
using namespace System;

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <include file="c:\davedata\jtest\xml_include.doc"/>
   // Try the following line instead:
   // /// <include file='xml_include.doc' path='MyDocs/MyMembers/*' />
   void MyMethod() {
   }
};   // C4637
```