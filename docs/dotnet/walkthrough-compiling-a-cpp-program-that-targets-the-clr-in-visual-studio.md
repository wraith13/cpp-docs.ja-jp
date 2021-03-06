---
title: コンパイルするには c++/cli プログラムを CLR を対象とします。
description: 使用して、MicrosoftC++ネイティブ プログラムと接続できるライブラリを作成するC++コードや .NET プログラムです。
ms.date: 04/23/2019
helpviewer_keywords:
- command-line applications [C++], managed code
- compiling programs [C++]
- Visual C++, managed code
- managed code [C++]
ms.assetid: 339f89df-a5d2-4040-831a-ddbe25b5dce4
ms.openlocfilehash: 8462b2b031bdcdebf65d58974c521d80e57d856d
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221805"
---
# <a name="walkthrough-compile-a-ccli-program-that-targets-the-clr-in-visual-studio"></a>チュートリアル: コンパイルするには c++/cli プログラムを Visual Studio で CLR を対象とします。

使用してC++/作成できる CLIC++ネイティブと .NET クラスを使用するプログラムC++型。 C++/CLI ネイティブをラップする Dll およびコンソール アプリケーションで使用されるC++コードし、.NET プログラムからアクセスできるようにします。 .NET ベースの Windows ユーザー インターフェイスを作成するには、使用C#または Visual Basic です。 

この手順では、C++ プログラムを入力するか、サンプル プログラムのいずれかを使用します。 この手順で使用するサンプル プログラムでは、textfile.txt という名前のテキスト ファイルを作成し、プロジェクト ディレクトリに保存します。

## <a name="prerequisites"></a>必須コンポーネント

- C++ 言語の基本の理解。
- Visual Studio 2017 以降では、 C++CLI のサポートは、オプションのコンポーネント/。 これをインストールするには、開く、 **Visual Studio インストーラー** Windows [スタート] メニューから。 確認します、**によるデスクトップ開発C++** タイルがチェックされ、し、 **(省略可能)** コンポーネント セクションもチェック **C++CLI サポート**します。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する

次の手順は、使用して Visual Studio のバージョンによって異なります。 左上隅の [バージョン] セレクターのこのページが正しく設定することを確認します。

::: moniker range="vs-2019"

### <a name="to-create-a-ccli-project-in-visual-studio-2019"></a>作成する、 C++/CLI プロジェクトで Visual Studio 2019

1. **ソリューション エクスプ ローラー**、開く上部を右クリックし、**新しいプロジェクトを作成** ダイアログ ボックス。

1. ダイアログ ボックスの上部にある次のように入力します。 **CLR** 、検索ボックスをクリック**CLR 空プロジェクト**結果リストから。 

1. 選択、**作成**プロジェクトを作成するボタンをクリックします。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-ccli-project-in-visual-studio-2017"></a>作成する、 C++/CLI プロジェクトで Visual Studio 2017

1. 新しいプロジェクトを作成します。 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

1. Visual C++ プロジェクトの種類から、**[CLR]**、**[CLR 空プロジェクト]** の順にクリックします。

1. プロジェクト名を入力します。 既定では、プロジェクトを含むソリューションは新しいプロジェクトと同じ名前になりますが、別の名前を入力してもかまいません。 必要に応じて、プロジェクトの場所として別の場所を入力することもできます。

1. **[OK]** をクリックして、新しいプロジェクトを作成します。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-ccli-project-in-visual-studio-2015"></a>作成する、 C++/CLI プロジェクトで Visual Studio 2015

1. 新しいプロジェクトを作成します。 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

1. Visual C++ プロジェクトの種類から、**[CLR]**、**[CLR 空プロジェクト]** の順にクリックします。

1. プロジェクト名を入力します。 既定では、プロジェクトを含むソリューションは新しいプロジェクトと同じ名前になりますが、別の名前を入力してもかまいません。 必要に応じて、プロジェクトの場所として別の場所を入力することもできます。

1. **[OK]** をクリックして、新しいプロジェクトを作成します。

::: moniker-end

## <a name="add-a-source-file"></a>ソース ファイルを追加します。

1. **ソリューション エクスプローラー**が表示されていない場合は、**[表示]** メニューの **[ソリューション エクスプローラー]** をクリックします。

1. プロジェクトに新しいソース ファイルを追加します。

   - **ソリューション エクスプローラー**で、**[ソース ファイル]** フォルダーを右クリックし、**[追加]** をポイントして、**[新しい項目]** をクリックします。

   - **[C++ ファイル (.cpp)]** をクリックしてファイル名を入力し、**[追加]** をクリックします。

   **ソリューション エクスプローラー**の**ソース ファイル** フォルダーに **.cpp** ファイルが表示されます。また、タブ付きウィンドウが表示され、ここでそのファイル内に含めるコードを入力します。

1. Visual Studio で新しく作成されたタブをクリックして、有効な Visual C++ プログラムを入力するか、サンプル プログラムのいずれかをコピーして貼り付けます。

   たとえば、[テキスト ファイルを作成する方法 (C++/CLI)](how-to-write-a-text-file-cpp-cli.md)のサンプル プログラム (プログラミング ガイドの「**ファイル処理と I/O**」ノード内) を使用できます。

   サンプル プログラムを使用する場合は、.NET オブジェクトを作成するときに、`new` の代わりに `gcnew`キーワードを使用することと、`gcnew` がポインター (`*`) ではなくハンドル (`^`) を返すことに注意してください。

   `StreamWriter^ sw = gcnew StreamWriter(fileName);`

   詳細についてはC++/CLI 構文を参照してください[Component Extensions for Runtime Platforms](../extensions/component-extensions-for-runtime-platforms.md)します。

1. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

   **[出力]** ウィンドウに、ビルド ログの場所やビルドの状態を示すメッセージなど、コンパイルの進行状況に関する情報が表示されます。

   ビルドを行わずに、プログラムを変更して実行する場合、ダイアログ ボックスにプロジェクトが有効期限切れであることが示される場合があります。 Visual Studio がアプリケーションをビルドするたびに入力を求めるのではなく、常にファイルの現在のバージョンを使用するようにする場合は、このダイアログでチェック ボックスを選択してから **[OK]** をクリックします。

1. **[デバッグ]** メニューの **[デバッグなしで開始]** をクリックします。

1. サンプル プログラムを使用した場合は、プログラムを実行するときに、テキスト ファイルが作成されたことを示すコマンド ウィンドウが表示されます。

   これで **textfile.txt** テキスト ファイルがプロジェクトに配置されました。 このファイルはメモ帳を使用して開くことができます。

   > [!NOTE]
   > 空の CLR プロジェクト テンプレートを選択すると、`/clr` コンパイラ オプションが自動的に設定されます。 これを確認するには、**ソリューション エクスプローラー**でプロジェクトを右クリックして、**[プロパティ]** をクリックしてから、**[構成プロパティ]** の **[全般]** ノードで **[共通言語ランタイム サポート]** オプションを確認します。

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[プロジェクトおよびビルド システム](../build/projects-and-build-systems-cpp.md)<br/>
