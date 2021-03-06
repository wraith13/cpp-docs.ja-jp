---
title: マルチスレッド:MFC プログラミングのヒント
ms.date: 08/27/2018
helpviewer_keywords:
- multithreading [C++], programming tips
- handle maps [C++]
- access control [C++], multithreading
- objects [C++], multiple threads and
- non-MFC threads [C++]
- threading [MFC], programming tips
- critical sections [C++]
- synchronization [C++], multithreading
- programming [C++], multithreaded
- communications [C++], between threads
- threading [C++], best practices
- troubleshooting [C++], multithreading
- Windows handle maps [C++]
ms.assetid: ad14cc70-c91c-4c24-942f-13a75e58bf8a
ms.openlocfilehash: deaf53d7b337fd33214bbcc4567e73bd33345d49
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511721"
---
# <a name="multithreading-mfc-programming-tips"></a>マルチスレッド:MFC プログラミングのヒント

マルチスレッドアプリケーションでは、操作が意図した順序で行われること、および複数のスレッドによってアクセスされるデータが破損していないことを確認するために、シングルスレッドアプリケーションよりも厳格に対処する必要があります。 このトピックでは、MFC (Microsoft Foundation Class) ライブラリを使用してマルチスレッド アプリケーションを開発する場合にこのような問題を回避する手法について説明します。

- [複数のスレッドからのオブジェクトへのアクセス](#_core_accessing_objects_from_multiple_threads)

- [Mfc 以外のスレッドからの MFC オブジェクトへのアクセス](#_core_accessing_mfc_objects_from_non.2d.mfc_threads)

- [Windows ハンドルマップ](#_core_windows_handle_maps)

- [スレッド間の通信](#_core_communicating_between_threads)

##  <a name="_core_accessing_objects_from_multiple_threads"></a>複数のスレッドからのオブジェクトへのアクセス

MFC オブジェクトは、単独ではスレッドセーフではありません。 MFC 同期クラスや、重要なセクションなどの適切な Win32 同期オブジェクトを使用しない限り、2つの個別のスレッドで同じオブジェクトを操作することはできません。 クリティカルセクションとその他の関連オブジェクトの詳細については、「Windows SDK での[同期](/windows/win32/Sync/synchronization)」を参照してください。

クラス ライブラリは内部的にクリティカル セクションを使って、デバッグ メモリの割り当てなどが使うグローバル データ構造を保護しています。

##  <a name="_core_accessing_mfc_objects_from_non.2d.mfc_threads"></a>Mfc 以外のスレッドからの MFC オブジェクトへのアクセス

[CWinThread](../mfc/reference/cwinthread-class.md)オブジェクトを使用する以外の方法でスレッドを作成するマルチスレッドアプリケーションがある場合、そのスレッドから他の MFC オブジェクトにアクセスすることはできません。 つまり、セカンダリスレッドから MFC オブジェクトにアクセスする場合は、マルチスレッドに関するページで[説明されているいずれかのメソッドを使用して、そのスレッドを作成する必要があります。ユーザーインターフェイススレッド](multithreading-creating-user-interface-threads.md)またはマルチ[スレッドの作成:ワーカースレッド](multithreading-creating-worker-threads.md)を作成しています。 ほかの方法では、マルチスレッド アプリケーションの実行に必要な内部変数をクラス ライブラリで初期化できません。

##  <a name="_core_windows_handle_maps"></a>Windows ハンドルマップ

通常、スレッドは自分自身が作成した MFC オブジェクトしかアクセスできません。 これは、Windows ハンドルの一時マップとパーマネント マップがスレッド ローカル ストレージに保持されており、複数のスレッドから同時にアクセスできないためです。 たとえば、あるワーカー スレッドで計算を行ってから、ドキュメント オブジェクトの `UpdateAllViews`メンバー関数を呼び出して、新しいデータに対するビューの格納先ウィンドウに反映させることはできません。 オブジェクトから`CWnd` hwnd へのマップはプライマリスレッドに対してローカルであるため、これはまったく効果がありません。 つまり、あるスレッドで Windows ハンドルから C++ オブジェクトへのマップが行われるときに、別のスレッドで同じハンドルを別の C++ オブジェクトにマップが行われることもあります。 あるスレッドで行われた変更は、ほかのスレッドには反映されません。

この問題を解決する方法はいくつかあります。 1つ目は、 C++オブジェクトではなく個々のハンドル (HWND など) をワーカースレッドに渡すことです。 ワーカー スレッドは該当する `FromHandle` メンバー関数を呼び出して、一時マップにオブジェクトを登録します。 を呼び出し`Attach`て、スレッドの永続的なマップにオブジェクトを追加することもできますが、これは、オブジェクトがスレッドよりも長く存在することが保証されている場合にのみ行う必要があります。

もう1つの方法は、ワーカースレッドが実行するさまざまなタスクに対応する新しいユーザー定義メッセージを作成し、を使用して`::PostMessage`これらのメッセージをアプリケーションのメインウィンドウにポストすることです。 この通信方法は、2 つの異なるアプリケーション間の対話動作に似ています。ただし、2 つのスレッドが同じアドレス空間を共有する点が異なります。

マップの処理の詳細については、「[テクニカルノート 3](../mfc/tn003-mapping-of-windows-handles-to-objects.md)」を参照してください。 スレッドローカルストレージの詳細については、「[スレッドローカルストレージ](/windows/win32/ProcThread/thread-local-storage)」および「Windows SDK での[スレッドローカルストレージの使用](/windows/win32/ProcThread/using-thread-local-storage)」を参照してください。

##  <a name="_core_communicating_between_threads"></a>スレッド間の通信

MFC には、スレッドからオブジェクトへのアクセスを同期化して、スレッドの安全性を保証するクラスがあります。 これらのクラスの使用方法に[ついては、「マルチスレッド:同期クラス](multithreading-how-to-use-the-synchronization-classes.md)と[マルチスレッドの使用方法:同期クラス](multithreading-when-to-use-the-synchronization-classes.md)を使用する場合。 これらのオブジェクトの詳細については、「Windows SDK での[同期](/windows/win32/Sync/synchronization)」を参照してください。

## <a name="see-also"></a>関連項目

[C++ と MFC を使用するマルチスレッド](multithreading-with-cpp-and-mfc.md)
