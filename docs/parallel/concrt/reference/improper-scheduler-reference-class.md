---
title: improper_scheduler_reference クラス
ms.date: 11/04/2016
f1_keywords:
- improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference
- CONCRT/concurrency::improper_scheduler_reference::improper_scheduler_reference
helpviewer_keywords:
- improper_scheduler_reference class
ms.assetid: 434a7512-7796-4255-92a7-f3bf71c6a7a7
ms.openlocfilehash: 121e61447775cdcb5d7f5f1187c5d4cc6b7d68b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262906"
---
# <a name="improperschedulerreference-class"></a>improper_scheduler_reference クラス

このクラスは、終了中の `Reference` オブジェクトで、スケジューラに属していないコンテキストから `Scheduler` メソッドが呼び出された場合にスローされる例外を表します。

## <a name="syntax"></a>構文

```
class improper_scheduler_reference : public std::exception;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[improper_scheduler_reference](#ctor)|オーバーロードされます。 `improper_scheduler_reference` オブジェクトを構築します。|

## <a name="inheritance-hierarchy"></a>継承階層

`exception`

`improper_scheduler_reference`

## <a name="requirements"></a>必要条件

**ヘッダー:** concrt.h

**名前空間:** concurrency

##  <a name="ctor"></a> improper_scheduler_reference

`improper_scheduler_reference` オブジェクトを構築します。

```
explicit _CRTIMP improper_scheduler_reference(_In_z_ const char* _Message) throw();

improper_scheduler_reference() throw();
```

### <a name="parameters"></a>パラメーター

*_Message*<br/>
エラーの説明メッセージ。

## <a name="see-also"></a>関連項目

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[Scheduler クラス](scheduler-class.md)
