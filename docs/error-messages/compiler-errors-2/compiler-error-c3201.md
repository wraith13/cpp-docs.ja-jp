---
title: コンパイラ エラー C3201
ms.date: 11/04/2016
f1_keywords:
- C3201
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
ms.openlocfilehash: 92e068103563f7427de7b394536e72b06fab3374
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402763"
---
# <a name="compiler-error-c3201"></a>コンパイラ エラー C3201

クラス テンプレート 'template' 用テンプレート パラメーター リストが、テンプレート パラメーター 'template' 用テンプレート パラメーター リストと一致しません。

テンプレート パラメーターを受け取らないクラス テンプレートに引数のクラス テンプレートが渡されました。または、既定のテンプレート引数にテンプレート引数と一致しない数値が渡されました。

```
// C3201.cpp
template<typename T1, typename T2>
class X1
{
};

template<template<typename T> class U = X1>   // C3201
class X2
{
};

template<template<typename T, typename V> class U = X1>   // OK
class X3
{
};
```