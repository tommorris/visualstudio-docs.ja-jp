---
title: DSL 定義への拡張機能の追加 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 07e133be-92ab-4936-a02b-45d2012bd0a6
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e3b8cb28edb6959511a0cfdf157e323d6706e5f6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537438"
---
# <a name="adding-extensions-to-dsl-definitions"></a>DSL 定義への拡張機能の追加
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[DSL 定義への拡張機能を追加する](https://docs.microsoft.com/visualstudio/modeling/adding-extensions-to-dsl-definitions)します。  
  
DSL 定義の拡張機能では、ドメイン固有言語 (DSL) の拡張機能のパッケージを作成できます。 Visual Studio Integration Extension (VSIX) に含まれている、DSL の拡張機能は、DSL と同じ方法でユーザーのコンピューターにインストールできます。 追加の機能を動的に有効になっている、実行時に無効になっています。 Dsl を拡張機能を明示的に設計する必要はありません、拡張機能後で、またはサード パーティによる拡張の DSL を変更することがなく設計します。  
  
 追加の機能を次に含めることができます。  
  
-   モデルとプレゼンテーション要素のプロパティ  
  
-   シェイプとコネクタのデコレーター  
  
-   クラス、リレーションシップ、図形とコネクタ  
  
-   検証制約  
  
-   ツールボックス項目とタブ  
  
 拡張の DSL のユーザーが作成し、追加の機能のインスタンスを含むモデルを保存し、これらは、適切な拡張機能がインストールされている他のユーザーで読み取ることができます。 拡張機能をインストールしていないユーザーは、追加の機能を使用できませんが、更新、追加の機能を失うことがなく、モデルを保存します。  
  
 サンプル コードとこの機能の詳細については、次を参照してください。、 [Visual Studio Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128) Web サイト。  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128)



