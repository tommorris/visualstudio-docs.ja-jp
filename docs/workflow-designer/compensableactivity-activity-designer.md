---
title: ワークフロー デザイナー - CompensableActivity アクティビティ デザイナー
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.CompensableActivity.UI
ms.assetid: e0340d89-d39e-4a52-8557-13e27040d7b5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d723b50fe0267939119239861c5ae951e01cd445
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2018
ms.locfileid: "36758293"
---
# <a name="compensableactivity-activity-designer"></a>CompensableActivity アクティビティ デザイナー

**CompensableActivity**作成および構成するアクティビティ デザイナーが使用される、<xref:System.Activities.Statements.CompensableActivity>アクティビティ。

## <a name="the-compensableactivity-activity"></a>CompensableActivity アクティビティ
 <xref:System.Activities.Statements.CompensableActivity> で、正常に完了した後に確認または補正できる作業単位を定義します。

### <a name="using-the-compensableactivity-activity-designer"></a>CompensableActivity アクティビティ デザイナーの使用
 **CompensableActivity**アクティビティ デザイナーが記載されて、**トランザクション**のカテゴリ**ツールボックス**します。 開くには**ツールボックス**を選択、**ツールボックス**ワークフロー デザイナーの左側にあるタブ。 または、選択**ツールボックス**から、**ビュー**メニューのまたはキーを押して**Ctrl**+**Alt** + **X**します。

 **CompensableActivity**からアクティビティ デザイナーをドラッグできる**ツールボックス**し、ワークフロー デザイナー画面にドロップします。 内のアクティビティ デザイナーをドロップすることが、<xref:System.Activities.Statements.Sequence>します。 アクティビティ デザイナーをドロップを作成、 <xref:System.Activities.Statements.CompensableActivity> 、既定値は、アクティビティ<xref:System.Activities.Activity.DisplayName%2A>CompensableActivity の。 編集、<xref:System.Activities.Activity.DisplayName%2A>のヘッダー値、 **CompensableActivity**アクティビティ デザイナー。 も編集できます、 **DisplayName**プロパティ グリッドのボックスです。

### <a name="the-compensableactivity-properties"></a>CompensableActivity のプロパティ
 次の表に、<xref:System.Activities.Statements.CompensableActivity> のプロパティと、デザイナーでのその使用方法を示します。 <xref:System.Activities.Activity.DisplayName%2A>と<xref:System.Activities.Activity%601.Result%2A>プロパティ グリッドでプロパティを編集できますが、その他のプロパティは、ワークフロー デザイナー画面で編集する必要があります。

|プロパティ名|必須|使用方法|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|<xref:System.Activities.Statements.CompensableActivity> アクティビティの省略可能な表示名。 既定値は CompensableActivity です。|
|<xref:System.Activities.Activity%601.Result%2A>|False|<xref:System.Activities.Statements.CompensableActivity> の戻り値を指定します。 このプロパティは、プロパティ グリッドで編集する必要があります。|
|<xref:System.Activities.Statements.CompensableActivity.Body%2A>|True|補正、取り消し、および確認の各ロジックの提供対象のアクティビティを指定します。 追加する、<xref:System.Activities.Statements.CompensableActivity.Body%2A>アクティビティからアクティビティのドロップ**ツールボックス**に、**本文**ボックスに、 **CompensableActivity**アクティビティ デザイナー。 「アクティビティをドロップここで」ヒント テキストを追加します。|
|<xref:System.Activities.Statements.CompensableActivity.CancellationHandler%2A>|False|取り消しがあるときに実行されるアクティビティを指定します。 アクティビティを追加するからデザイナーをドロップ**ツールボックス**に、 **CancellationHandler**ボックスに、 **CompensableActivity**アクティビティ デザイナー。 「削除アクティビティここ」ヒント テキストを追加します。|
|<xref:System.Activities.Statements.CompensableActivity.CompensationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> アクティビティの補正を行うときに実行されるアクティビティを指定します。 このハンドラーは、<xref:System.Activities.Statements.Compensate> アクティビティを使用して明示的に呼び出すことができます。<br /><br /> アクティビティを追加するからアクティビティ デザイナーをドロップ**ツールボックス**に、 **CompensationHandler**ボックスに、 **CompensableActivity**アクティビティ デザイナー。 「削除アクティビティここ」ヒント テキストを追加します。|
|<xref:System.Activities.Statements.CompensableActivity.ConfirmationHandler%2A>|False|<xref:System.Activities.Statements.CompensableActivity.Body%2A> アクティビティを確認するときに実行されるアクティビティを指定します。 このハンドラーは、<xref:System.Activities.Statements.Confirm> アクティビティを使用して明示的に呼び出すことができます。<br /><br /> アクティビティを追加するからアクティビティ デザイナーをドロップ**ツールボックス**に、 **ConfirmationHandler**ボックスに、 **CompensableActivity**アクティビティ デザイナー。 「削除アクティビティここ」ヒント テキストを追加します。|

## <a name="see-also"></a>関連項目

- [トランザクション](../workflow-designer/transaction-activity-designers.md)
- [CancellationScope](../workflow-designer/cancellationscope-activity-designer.md)
- [補正](../workflow-designer/compensate-activity-designer.md)
- [確認します](../workflow-designer/confirm-activity-designer.md)
- [TransactionScope](../workflow-designer/transactionscope-activity-designer.md)