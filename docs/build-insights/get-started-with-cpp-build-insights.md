---
title: Build Insights をC++使ってみる
description: ビルドインサイトのC++一部であるビルド時のパフォーマンス分析ツールを使用する方法の概要について説明します。
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9c31d317cd7b9c6465362e3e532db2128303f602
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633226"
---
# <a name="get-started-with-c-build-insights"></a>Build Insights をC++使ってみる

::: moniker range="<=vs-2017"

Visual C++ Studio 2019 では、Build Insights ツールを使用できます。 そのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range="vs-2019"

C++Build Insights は、Microsoft Visual C++ (MSVC) ツールチェーンの可視性を向上させるツールのコレクションです。 これらのツールは、 C++ビルドに関するデータを収集し、次のような一般的な質問に回答するのに役立つ形式で提示します。

- ビルドは十分に並列化されていますか。
- プリコンパイル済みヘッダー (PCH) には何を含める必要がありますか。
- ビルドの速度を向上させるために、特に注目する必要のあるボトルネックはありますか。

このテクノロジの2つの主要なコンポーネントは、コマンドラインユーティリティ*vcperf*と、Windows Performance ANALYZER (WPA) トレースビューアー用のアドインです。 ユーティリティは、ビルドのトレースを収集するために使用されます。また、アドインでは、このユーティリティを WPA で表示できます。 これらの2つのツールの使用を開始するには、次の手順に従います。

## <a name="step-1-install-and-configure-windows-performance-analyzer"></a>手順 1: Windows パフォーマンスアナライザーをインストールして構成する

WPA は、Windows アセスメント & amp; デプロイメントキット (ADK) で利用可能なトレースビューアーです。 これは、Visual Studio インストーラーを使用してインストールできるコンポーネントの一部ではない、独立したユーティリティです。

現在、Build Insights をサポートC++するバージョンの WPA は、Windows ADK Insider Preview でのみ使用できます。 このプレビューにアクセスするには、 [Windows Insider program](https://insider.windows.com)にサインアップする必要があります。 Windows ADK preview を入手するために、Windows 10 Insider Preview オペレーティングシステムをインストールする必要はありません。 Microsoft アカウントを登録する必要があるのは、Windows Insider Program だけです。

### <a name="to-download-and-install-wpa"></a>WPA をダウンロードしてインストールするには

1. Windows ADK Insider Preview[ダウンロードページ](https://www.microsoft.com/software-download/windowsinsiderpreviewADK)に移動します。

1. Windows ADK Insider Preview をダウンロードします。 ディスクイメージです。

1. ディスクイメージを開き、 *adksetup*インストーラーを実行します。

1. インストールする機能の入力を求められたら、 **[Windows パフォーマンスツールキット]** を選択します。 必要に応じて他の機能を選択することもできますが、WPA のインストールは必須ではありません。

   ![Windows Performance Analyzer インストーラーの [機能の選択] 画面](media/wpa-installation.png)

### <a name="configuration-steps"></a>ビルドインサイトを構成するには

1. WPA を起動します。

1. [テーブルの選択 **] > [** **テーブル (試験段階)** ] を選択します。

1. **[診断]** セクションまで下にスクロールします。

1. すべての MSVC Build Insights ビューを選択します。

   ![Windows Performance Analyzer のテーブル選択パネル](media/wpa-configuration.png)

## <a name="step-2-trace-your-build-with-vcperfexe"></a>手順 2: vcperf を使用してビルドをトレースする

ビルドインC++サイトデータを表示するには、次の手順に従って、まずそのデータをトレースファイルに収集します。

1. 管理者モードで Visual Studio 2019 用のネイティブツールまたはクロスツール開発者コマンドプロンプトを開きます。 (スタート メニュー項目を右クリックし、**その他** > **管理者として実行** を選択します)。

1. コマンドプロンプトウィンドウで、次のコマンドを入力します。

   **vcperf の/start の_セッション名_**

   セッション*名を選択してください*。

1. 通常どおりにプロジェクトをビルドします。 同じコマンドプロンプトウィンドウを使用してビルドする必要はありません。

1. コマンドプロンプトウィンドウで、次のコマンドを入力します。

   **vcperf. ファイル_名_ _. .etl_**

   *前のセッション名に選択*したのと同じセッション名を使用します。 *Tracefile .etl*トレースファイルに適切な名前を選択します。

開発者コマンドプロンプトウィンドウで、一般的な*vcperf*コマンドシーケンスは次のようになります。

![単純な vcperf の使用シナリオ](media/vcperf-simple-usage.png)

### <a name="important-notes-about-vcperfexe"></a>Vcperf に関する重要な注意事項

- *Vcperf*のトレースを開始または停止するには、管理者特権が必要です。 **[管理者として実行]** を使用して開いた開発者コマンドプロンプトウィンドウを使用します。

- コンピューター上で実行できるトレースセッションは一度に1つだけです。

- トレースを開始するために使用したセッション名を忘れないようにしてください。 実行中のセッションを停止すると、名前がわからなくなることがあります。

- *Cl.exe*や setup.exe と同じよう*に、* コマンドラインユーティリティ*vcperf*は MSVC のインストールに含まれています。 このコンポーネントを取得するために追加の手順は必要ありません。

- *vcperf*は、システムで実行されているすべての MSVC ツールに関する情報を収集します。 その結果、トレースの収集に使用したのと同じコマンドプロンプトからビルドを開始する必要がなくなります。 プロジェクトは、別のコマンドプロンプトから、または Visual Studio でもビルドできます。

## <a name="step-3-view-your-trace-in-windows-performance-analyzer"></a>手順 3: Windows パフォーマンスアナライザーでトレースを表示する

WPA を起動し、先ほど収集したトレースを開きます。 WPA はこれをC++ Build Insights トレースとして認識し、左側のグラフエクスプローラーパネルに次のビューを表示する必要があります。

- ビルド エクスプローラー
- ファイル
- 機能

これらのビューが表示されない場合は、[手順 1](#configuration-steps). で説明したように、WPA が正しく構成されていることを再確認します。 次に示すように、右側の空の分析ウィンドウにビューをドラッグすると、ビルドデータを表示できます。

![Windows Performance C++ Analyzer でのビルドインサイトトレースの表示](media/wpa-viewing-trace.gif)

その他のビューは、グラフエクスプローラーパネルで使用できます。 含まれている情報に関心がある場合は、それらを [分析] ウィンドウにドラッグします。 1つは CPU (サンプリングされた) ビューで、ビルド全体の CPU 使用率を示しています。

## <a name="more-information"></a>説明

[Windows Performance Analyzer の基本](wpa-basics.md)\
ビルドトレースの分析に役立つ一般的な WPA 操作について説明します。

[vcperf のリファレンス](vcperf-reference.md)\
*Vcperf .exe*コマンドリファレンスには、使用可能なすべてのコマンドオプションが一覧表示されます。

[Windows パフォーマンスアナライザービューの参照](wpa-views-reference.md)\
WPA の Build Insights ビューの詳細にC++ついては、こちらの記事を参照してください。

[Windows パフォーマンスアナライザー](/windows-hardware/test/wpt/windows-performance-analyzer)の\
公式の WPA ドキュメントサイト。

::: moniker-end
