---
title: オートメーションクライアント:タイプライブラリの使用
ms.date: 11/04/2016
f1_keywords:
- MkTypLib
helpviewer_keywords:
- clients, Automation
- dispatch class [MFC]
- Automation clients, type libraries
- type libraries, Automation clients
- ODL (Object Description Language)
- ODL files
- classes [MFC], dispatch
- MkTypLib tool
- .odl files
ms.assetid: d405bc47-118d-4786-b371-920d035b2047
ms.openlocfilehash: 480f8fca46b13d445f372311ed837475c71a1e9d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509218"
---
# <a name="automation-clients-using-type-libraries"></a>オートメーションクライアント:タイプライブラリの使用

クライアントがサーバーのオブジェクトを操作する場合は、オートメーションクライアントにサーバーオブジェクトのプロパティとメソッドに関する情報が含まれている必要があります。 プロパティにはデータ型があります。多くの場合、メソッドは値を返し、パラメーターを受け取ります。 クライアントは、サーバーオブジェクト型に静的にバインドするために、これらのすべてのデータ型に関する情報を必要とします。

この型情報は、いくつかの方法で知らせることができます。 タイプライブラリを作成することをお勧めします。

[MkTypLib](/windows/win32/Midl/differences-between-midl-and-mktyplib)の詳細については、Windows SDK を参照してください。

ビジュアルC++では、タイプライブラリファイルを読み取り、 [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md)から派生したディスパッチクラスを作成できます。 そのクラスのオブジェクトには、サーバーオブジェクトとの間でプロパティと操作が複製されます。 アプリケーションはこのオブジェクトのプロパティと操作を呼び出し、から`COleDispatchDriver`継承された機能はこれらの呼び出しを OLE システムにルーティングし、次にサーバーオブジェクトにルーティングします。

プロジェクトC++の作成時にオートメーションを含めることを選択した場合、ビジュアルによって自動的にこのタイプライブラリファイルが保持されます。 各ビルドの一部として、.tlb ファイルは MkTypLib を使用してビルドされます。

### <a name="to-create-a-dispatch-class-from-a-type-library-tlb-file"></a>タイプライブラリ (.tlb) ファイルからディスパッチクラスを作成するには

1. クラスビューまたはソリューションエクスプローラーで、プロジェクトを右クリックして [**追加**] をクリックし、ショートカットメニューの [**クラスの追加**] をクリックします。


2. **クラスの追加**ダイアログ ボックスで、 左側の**Visual C++/MFC**フォルダを選択します。 右側のペインの **TypeLib からの MFC クラス**アイコンを選択し、**開く**をクリックします。


1. [ **Typelib からクラスを追加ウィザード**] ダイアログボックスで、[**使用できるタイプ**ライブラリ] ドロップダウンリストからタイプライブラリを選択します。 [**インターフェイス**] ボックスには、選択したタイプライブラリで使用可能なインターフェイスが表示されます。

    > [!NOTE]
    >  複数のタイプライブラリからインターフェイスを選択できます。

   インターフェイスを選択するには、それらをダブルクリックするか、[**追加**] ボタンをクリックします。 これを行うと、[生成された**クラス**] ボックスにディスパッチクラスの名前が表示されます。 クラス名は、 `Class`ボックスで編集できます。

   [**ファイル**] ボックスに、クラスが宣言されるファイルが表示されます。 (このファイル名も編集できます)。 また、既存のファイルまたはプロジェクトディレクトリ以外のディレクトリに記述されているヘッダーおよび実装情報を使用する場合は、[参照] ボタンを使用して他のファイルを選択することもできます。

    > [!NOTE]
    >  選択したインターフェイスのすべてのディスパッチクラスは、ここで指定したファイルに格納されます。 インターフェイスを別のヘッダーで宣言する場合は、作成する各ヘッダーファイルに対してこのウィザードを実行する必要があります。

    > [!NOTE]
    >  一部のタイプライブラリ情報は、を使用してファイルに格納できます。DLL、。OCX、または.OLB ファイル拡張子。

1. **[完了]** をクリックします。

   次に、指定されたクラスとファイル名を使用して、ディスパッチクラスのコードが書き込まれます。

## <a name="see-also"></a>関連項目

[オートメーション クライアント](../mfc/automation-clients.md)
