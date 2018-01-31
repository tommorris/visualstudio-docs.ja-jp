---
title: "Visual Studio デバッガーでブレークポイントをトラブルシューティングする |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/23/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "0"
author: carpediemma
ms.author: emrou
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a59a5448cb9ceb9aa4ac5578e9234c1a9972a15a
ms.sourcegitcommit: 062795f922e7b59fe00d3d95a01a9a8a28840017
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2018
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Visual Studio デバッガーでブレークポイントをトラブルシューティングします。

## <a name="breakpoint-warnings"></a>ブレークポイントの警告

ブレークポイントが 2 つの可能な表示状態でデバッグする場合、: 純色の赤い円と中空 (入力白) 円です。 デバッガーが正常にターゲット プロセスでブレークポイントを設定できる場合は、その実線の赤い円が維持されます。 ブレークポイントが中空の円の場合は、ブレークポイントが無効であるか、ブレークポイントを設定しようとするときに警告が発生しました。 違いを特定するのには、ブレークポイントをポイントし、警告がないかどうか。

次の 2 つのセクションでは、著名な警告およびそれらを修正する方法について説明します。 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>「シンボルが読み込まれていないこのドキュメントの」 

移動して、**モジュール**ウィンドウ (**デバッグ** > **Windows** > **モジュール**) し、モジュールかどうかを確認読み込まれます。  
* モジュールが読み込まれている場合は、確認、**シンボルの状態**シンボルが読み込まれているかどうかを表示する列。 
  * シンボルが読み込まれていない場合は、問題を診断するシンボルの状態を確認します。 内のモジュールのコンテキスト メニューから、**モジュール**ウィンドウで、をクリックして**シンボルの読み込み情報.**を再試行し、シンボルの読み込みにデバッガーを検索する場所を参照してください。 シンボルの読み込みの詳細については、次を参照してください。[指定シンボル (.pdb) とソース ファイル](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)です。  
  * シンボルが読み込まれる場合は、pdb ファイルに、ソース ファイルに関する情報が含まれていないことを意味します。 これらは、いくつかの原因が考えられます。 
    * ソース ファイルを最近追加した場合は、モジュールの最新のバージョンが読み込まれていることを確認します。  
    * 使用して削除された Pdb を作成することは、 **/PDBSTRIPPED**リンカー オプション。 削除された Pdb では、ソース ファイルの情報は含まれません。 使用する完全な PDB および除去された pdb ファイルではないことを確認します。  
    * PDB ファイルが部分的に破損しています。 ファイルを削除してから、問題を解決する場合は、このモジュールのクリーン ビルドを実行します。 

* モジュールが読み込まれていない場合は、原因を見つけるには、次を確認します。 
  * 適切なプロセスをデバッグしていることを確認します。 
  * 適切なコードをデバッグしていることを確認します。 デバッガーでデバッグするように構成コードの種類を知ることができます、**プロセス**ウィンドウ (**デバッグ** > **Windows**  >  **プロセス**)。 たとえば、c# コードをデバッグする場合は、ことを確認、デバッガーが構成されている .NET Framework の適切な型 (たとえば、管理 (v4\*) 管理されていると (v2\*/v3\*) マネージ (CoreCLR) ではなく)。 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… 現在のソース コードが... に組み込まれているバージョンと異なる" 

ソース ファイルが変更され、デバッグ中のコードと一致しなく、デバッガーは設定しませんブレークポイント、コードで既定では。 通常、ソース ファイルを変更すると、ソース コードを再構築されなかった場合に、この問題が発生します。 この問題を解決するには、プロジェクトをリビルドします。 ビルド システムでは、プロジェクトの場合は最新の状態は既にと思われる、ソース ファイルを再度保存するかを再構築またはプロジェクトのクリーンアップしてビルドする前に出力をビルドするプロジェクト システムを強制することができます。 

まれなシナリオは、一致するソース コードをしなくてもデバッグすることがあります。 これにより、非常に複雑になる場合のデバッグ エクスペリエンスにつながることができます、続行する方法がこのようにしてください。  

これらの安全性チェックを無効にするには、次のいずれかの操作を行います。 
* 単一のブレークポイントを変更するには、エディターでブレークポイント アイコンにマウスを設定 (歯車) のアイコンをクリックします。 エディター ウィンドウが追加されます。 表示のみ ウィンドウの上部にあるブレークポイントの位置を示すハイパーリンクがあります。 ブレークポイントの場所の変更を許可して、確認するには、ハイパーリンクをクリックして**、ソース コードを許可する元と異なる**です。
* すべてのブレークポイントには、この設定を変更するには**デバッグ** > **オプションと設定**です。 **[デバッグ] / [全般]** ページで、 **[元のバージョンと完全に一致するソース ファイルを必要とする]** オプションをオフにします。 完了したら、このオプションを再度有効にすることを確認デバッグします。 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>ブレークポイントが正常に設定されています (警告なし) がヒットしませんでした。 

このセクションでは、すべての警告が表示されない、デバッガー – ブレークポイントがアクティブにデバッグ中に純色の赤い円がまだブレークポイントがヒットされていないときに問題のトラブルシューティング情報を提供します。 

確認する点を次に示します。 
1. 複数のプロセスまたは複数のコンピューターで、コードの実行をデバッグする場合、適切なプロセスまたはコンピューターを確認します。  
2. コードが実行されていることを確認します。 呼び出しを追加するにはこれをテストする方法は簡単`System.Diagnostics.Debugger.Break`(C# および VB) または`__debugbreak`(C++) コードのブレークポイントを設定し、プロジェクトをリビルドする先の行にします。 
3. 最適化されたコードをデバッグしている場合を確認してください、ブレークポイントが設定されている関数はありませんされている別の関数にインライン展開されています。 `Debugger.Break`もこれをテストする前のチェックで説明したテストを操作できます。 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>ブレークポイントを削除したが、デバッグを再実行するとヒットし続ける 

デバッグ中にブレークポイントを削除した場合は、デバッグを開始するときにもう一度をブレークポイントにヒット可能性があります。 このブレークポイントのヒットを停止するには、ブレークポイントのすべてのインスタンスが **[ブレークポイント]** ウィンドウから削除されていることを確認します。  