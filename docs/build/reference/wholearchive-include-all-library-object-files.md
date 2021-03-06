---
title: /WHOLEARCHIVE (すべてのライブラリ オブジェクト ファイルを含む)
ms.date: 11/04/2016
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
ms.openlocfilehash: db99816b18110b424647603196040997044e7fbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316432"
---
# <a name="wholearchive-include-all-library-object-files"></a>/WHOLEARCHIVE (すべてのライブラリ オブジェクト ファイルを含む)

リンクされた実行可能ファイルでのスタティック ライブラリですべてのオブジェクト ファイルを含めるようにリンカーを強制します。

## <a name="syntax"></a>構文

> /WHOLEARCHIVE[:*library*]

## <a name="remarks"></a>Remarks

/WHOLEARCHIVE オプションは、リンカーに指定された静的ライブラリのいずれかからすべてのオブジェクト ファイルを含めるまたはライブラリが指定されていない場合、リンクに指定されたすべての静的ライブラリからコマンドを強制します。 複数のライブラリの/WHOLEARCHIVE オプションを指定するには、リンカー コマンドラインに/WHOLEARCHIVE スイッチが 1 つ以上を使用できます。 既定では、実行可能ファイルには、他のオブジェクト ファイルで参照されているシンボルをエクスポートする場合にのみ、リンカーはリンクされた出力オブジェクト ファイルを含めます。 /WHOLEARCHIVE オプションでは、リンカーのコマンドラインで個別に指定した場合と、スタティック ライブラリでアーカイブされたすべてのオブジェクト ファイルを扱うリンカーを使用します。

/WHOLEARCHIVE オプションは、静的ライブラリからのすべてのシンボルを再エクスポートに使用できます。 これにより、すべてのライブラリ コード、リソース、およびメタデータが含まれる 1 つ以上の静的ライブラリからコンポーネントを作成するときになっていることを確認することができます。 警告 LNK4264 スタティック ライブラリを作成するときにエクスポート用の Windows ランタイム コンポーネントを含んでいる場合は、別のコンポーネントまたはアプリにそのライブラリをリンクするときに、/WHOLEARCHIVE オプションを使用します。

/WHOLEARCHIVE オプションは、Visual Studio 2015 Update 2 で導入されました。

### <a name="to-set-this-linker-option-in-visual-studio"></a>このリンカー オプションを Visual Studio で設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**コマンドライン**プロパティ ページ**構成プロパティ**、**リンカー**します。

1. /WHOLEARCHIVE オプションを追加、**追加オプション**テキスト ボックス。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
