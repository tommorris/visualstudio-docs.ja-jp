---
title: 'CA1725: パラメーター名は基本宣言と同一でなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1f7c8a71d91468129703b0d2101f7ab0e7527fa
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550720"
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: パラメーター名は基本宣言と同一でなければなりません
|||
|-|-|
|TypeName|ParameterNamesShouldMatchBaseDeclaration|
|CheckId|CA1725|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照できるメソッド オーバーライドでのパラメーターの名前は、メソッドの基本宣言またはメソッドのインターフェイス宣言のパラメーターの名前のパラメーターの名前と一致しません。

## <a name="rule-description"></a>規則の説明
 オーバーライド階層のパラメーターに対する一貫性のある名前付けによって、メソッド オーバーライドの有用性が高まります。 派生メソッドのパラメーター名が基本宣言のパラメーター名と異なる場合、メソッドが基本メソッドのオーバーライドであるか、またはメソッドの新しいオーバーライドであるかについて混乱が生じる可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、基本宣言と一致するパラメーターの名前を変更します。 修正プログラムは、COM 参照可能なメソッドの互換性に影響する変更です。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 以前に出荷されたライブラリ内の COM 参照可能なメソッドを除き、この規則による警告を抑制しないでください。