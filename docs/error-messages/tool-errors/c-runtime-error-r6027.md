---
title: C ランタイム エラー R6027
ms.date: 11/04/2016
f1_keywords:
- R6027
helpviewer_keywords:
- R6027
ms.assetid: c06a62b3-08d9-4bf5-bcad-8340ec552f69
ms.openlocfilehash: 2884f148091d9407d3229f0690a161639b5195e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395145"
---
# <a name="c-runtime-error-r6027"></a>C ランタイム エラー R6027

lowio 初期化領域が足りません。

> [!NOTE]
> アプリの実行中にこのエラー メッセージが発生した場合、アプリがシャット ダウン、内部メモリの問題があるためです。 このエラーは、いくつかの理由がありますが、通常原因が、非常に低いメモリ条件。 アプリでのバグを使用する Visual C ライブラリの破損またはドライバーにも発生することができます。
>
> このエラーを解決するには、次の手順を試してみます。
>
> - その他の実行中のアプリケーションを閉じるか、メモリを解放するため、コンピューターを再起動します。
> - 使用して、**アプリおよび機能**または**プログラムと機能**ページで、**コントロール パネルの **を修復またはプログラムを再インストールします。
> - 別のアプリまたはドライバーの最新のインストール前に、アプリが動作している場合は、使用、**アプリおよび機能**または**プログラムと機能**ページで、**コントロール パネルの **を削除する、新しいアプリまたはドライバー、およびアプリをもう一度やり直してください。
> - 使用して、**アプリおよび機能**または**プログラムと機能**ページで、**コントロール パネルの **修復または Microsoft Visual C Redistributable のすべてのコピーを再インストールします。
> - 確認**Windows Update**で、**コントロール パネルの **ソフトウェアの更新。
> - アプリの更新バージョンを確認します。 問題が解決しない場合は、アプリのベンダーにお問い合わせください。

**プログラマのための情報**

このエラーは、C ランタイムで低レベルの I/O のサポートを初期化するために使用できる十分な空きメモリがない場合に発生します。 このエラーは、アプリの起動時に通常発生します。 アプリとドライバーと dll を読み込むことが起動時に、ヒープを破損しないことを確認します。