---
title: カスタム ビューの管理オブジェクトの作成 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.data.elements
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- data types [C#], custom
- custom data types
- managed code, custom data types
- autoexp.dat file
- mcee_cs.dat file
- debugger, expanding data types
- mcee_mc.dat file
ms.assetid: 9969e9b2-9008-4729-8a14-0d6deaa61576
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 970051c5f53c152ea6fee334c3c1f856172b5ed9
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2018
ms.locfileid: "44280546"
---
# <a name="create-custom-views-of-managed-objects"></a>.managed オブジェクトのカスタム ビューの作成
Visual Studio でデバッガーの変数ウィンドウにデータ型を表示する方法をカスタマイズできます。  
  
## <a name="attributes"></a>属性  
 C# および Visual Basic では、<xref:System.Diagnostics.DebuggerTypeProxyAttribute>、<xref:System.Diagnostics.DebuggerDisplayAttribute>、および <xref:System.Diagnostics.DebuggerBrowsableAttribute> を使用して、カスタム データの展開を追加できます。  
  
 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] コードでは、Visual Basic は DebuggerBrowsable 属性をサポートしません。 この制限は、.NET Framework の新しいバージョンで解除されています。  
  
## <a name="visualizers"></a>ビジュアライザー  
 マネージド データ型を表示するには、ビジュアライザーを記述します。 詳細については、次を参照してください。[方法: ビジュアライザーを記述する](../debugger/how-to-write-a-visualizer.md)します。  
  
## <a name="native-code"></a>ネイティブ コード  
 ネイティブ コードの場合、カスタム データ型の展開を autoexp.dat ファイルに追加します。autoexp.dat は、Program Files\Microsoft Visual Studio 11.0\Common7\Packages\Debugger ディレクトリにあります。 `autoexp` 規則の記述手順は、このファイルに含まれています。  
  
> [!CAUTION]
>  このファイルの構造と自動展開規則の構文は、Visual Studio のリリースごとに異なる可能性があります。  
  
 また、ネイティブ型の表示は、式エバリュエーター アドインを記述してカスタマイズできます。 詳細については、次を参照してください。 [EEAddIn サンプル: デバッグ式エバリュエーター アドイン](https://msdn.microsoft.com/library/d4f6b068-c812-45bc-9ec0-7e0363c4bb9e)します。  
  
## <a name="see-also"></a>関連項目  
 [DebuggerTypeProxy 属性の使用](../debugger/using-debuggertypeproxy-attribute.md)   
 [DebuggerDisplay 属性の使用](../debugger/using-the-debuggerdisplay-attribute.md)   
 [ウォッチ ウィンドウと [クイック ウォッチ] の Windows](../debugger/watch-and-quickwatch-windows.md)   
 [デバッガー表示属性によるデバッグ機能の拡張](/dotnet/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes)