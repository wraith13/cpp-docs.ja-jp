---
title: コンパイラ エラー C3738
ms.date: 11/04/2016
f1_keywords:
- C3738
helpviewer_keywords:
- C3738
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
ms.openlocfilehash: e313c7d66bc030183e330dd961fad2fb35f02ac2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327809"
---
# <a name="compiler-error-c3738"></a>コンパイラ エラー C3738

'calling_convention': 明示的なインスタンス化の呼び出し規約がインスタンス化されているテンプレートの一致する必要があります

明示的なインスタンス化の呼び出し規約を指定しないことをお勧めします。 、必要な場合、呼び出し規約に一致する必要があります。

## <a name="example"></a>例

次の例では、C3738 が生成されます。

```
// C3738.cpp
// compile with: /clr
// processor: x86
#include <stdio.h>
template< class T >
void f ( T arg ) {   // by default calling convention is __cdecl
   printf ( "f: %s\n", __FUNCSIG__ );
}

template
void __stdcall f< int > ( int arg );   // C3738
// try the following line instead
// void f< int > ( int arg );

int main () {
   f(1);
   f< int > ( 1 );
}
```