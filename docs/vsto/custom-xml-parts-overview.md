---
title: カスタム XML 部分の概要
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom XML parts [Office development in Visual Studio], about
- Office Open XML Formats [Office development in Visual Studio]
- custom XML parts [Office development in Visual Studio]
- embedding XML data in documents [Office development in Visual Studio]
- XML parts [Office development in Visual Studio]
- XML file formats [Office development in Visual Studio]
- data [Office development in Visual Studio], custom XML parts
- Office documents [Office development in Visual Studio, custom XML parts
- XML [Office development in Visual Studio], custom XML parts
- Word [Office development in Visual Studio], custom XML parts
- Excel [Office development in Visual Studio], custom XML parts
- documents [Office development in Visual Studio], custom XML parts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e4c32f3a9b0f0c09b7e7b58aa4c424630326d122
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "35671867"
---
# <a name="custom-xml-parts-overview"></a>カスタム XML 部分の概要
  一部の Microsoft Office アプリケーションのドキュメントに XML データを埋め込むことができます。 データがという名前をドキュメントに XML データを埋め込むときに、*カスタム XML 部分*します。  
  
 Visual Studio で VSTO アドインまたはドキュメント レベルのソリューションを使用して、ドキュメントのカスタム XML 部分を作成または変更できます。 カスタム XML 部分を作成または変更するために Microsoft Office アプリケーションを開始する必要はありません。  
  
 **適用されます:** Excel、PowerPoint、および Word のドキュメント レベルのプロジェクトおよび VSTO アドインのプロジェクトに、このトピックの情報には適用されます。 詳細については、次を参照してください。 [Office アプリケーションおよびプロジェクトの種類で使用できる機能](../vsto/features-available-by-office-application-and-project-type.md)します。  
  
> [!NOTE]  
>  Visual Studio では、ドキュメント レベルのカスタマイズ内のデータ オブジェクトをキャッシュすることもできます。 いくつかの類似点はありますが、この機能はカスタム XML 部分とは異なります。 詳細については、次を参照してください。[ドキュメント レベルのカスタマイズでキャッシュされたデータ](../vsto/cached-data-in-document-level-customizations.md)します。  
  
## <a name="understand-custom-xml-parts"></a>カスタム XML 部分を理解します。  
 カスタム XML 部分は、2007 Microsoft Office system で Open XML 形式とともに導入されました。 これらの形式は、Excel、PowerPoint、および Word の新しい XML ベースのファイル形式を含める (など *.xlsx*、 *.pptx*、および *.docx*)。 これらの形式でドキュメントが XML ファイルで構成されます (とも呼ばれます*XML パーツ*) ZIP アーカイブ内のフォルダーに編成されます。 XML 部分のほとんどは、ドキュメントの構造と状態を定義するのに役立つ組み込みの部分です。 ただし、ドキュメントにはカスタム XML 部分を含めることができ、ユーザーはこれを使用して、ドキュメントに任意の XML データを格納できます。  
  
 XML ファイル形式が以前のバイナリ ファイル形式では実現できない方法でドキュメントを操作するアプリケーションを有効にする (など *.xls*、 *.ppt*、および *.doc*)。 ZIP アーカイブを読み取ることができるすべてのアプリケーションは、Microsoft Office がインストールされていない場合でも、ドキュメントの内容を検証し、変更できます。  
  
 Open XML およびカスタム XML 部分の構造の詳細については、次の記事をご覧ください。  
  
-   [Office (2007) Open XML ファイル形式の概要](http://msdn.microsoft.com/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [方法: Open XML 形式のドキュメントの操作](http://msdn.microsoft.com/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [チュートリアル: Word 2007 の XML の形式](http://msdn.microsoft.com/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Open XML 形式を使用して Word 2007 ドキュメントを作成します。](http://msdn.microsoft.com/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel、Word、および PowerPoint ではバイナリ ファイル形式で保存されているドキュメント内のカスタム XML 部分を使用することもできます。 ただし、バイナリ形式でドキュメントを保存する場合は、Microsoft Office アプリケーションを起動せずにカスタム XML 部分を追加または変更することはできません。  
  
## <a name="create-and-modify-custom-xml-parts"></a>作成およびカスタム XML 部分を変更します。  
 ドキュメントが Office アプリケーションで開いているとき、またはドキュメントが閉じているとき (Microsoft Office がインストールされていない場合でも)、カスタム XML 部分を作成または変更できます。  
  
### <a name="modify-xml-parts-while-the-office-application-is-running"></a>Office アプリケーションの実行中の XML 部分を変更します。  
 ドキュメント レベルのカスタマイズまたは VSTO アドインを使用して、カスタム XML 部分を操作することができます。 ドキュメント レベルのカスタマイズを使用している場合は、通常、カスタマイズされたドキュメント内にあるカスタム XML 部分を操作します。 VSTO アドインを使用する場合は、作成または、アプリケーションで開いている任意のドキュメントのカスタム XML 部分を変更することができます。  
  
 Visual Studio を使用してカスタム XML 部分を作成するには、新しい <xref:Microsoft.Office.Core.CustomXMLPart> をドキュメントの <xref:Microsoft.Office.Core.CustomXMLParts> コレクションに追加します。 詳細については、次のトピックを参照してください。  
  
-   [方法: ドキュメント レベルのカスタマイズにカスタム XML 部分を追加します。](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [方法: VSTO アドインを使用して、カスタム XML 部分をドキュメントに追加](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### <a name="modify-xml-parts-without-starting-the-office-application"></a>Office アプリケーションを起動せずに XML 部分を変更します。  
 Excel、PowerPoint、または Word を起動しないでカスタム XML 部分を変更できます。 これは、Microsoft Office アプリケーションがインストールされていないサーバーなどのコンピューターで、ドキュメント内の XML データを使用する場合に便利です。  
  
 Microsoft Office を起動せずにカスタム XML 部分を追加するには Open XML SDK のクラスを使用します。 これらのクラスは、Office ドキュメントに固有の Open XML コンテンツにアクセスするために設計されています。 使用する Excel ブックにカスタム XML 部分を追加するなど、 [AddNewPart\<T >](http://msdn.microsoft.com/47c348c0-77ab-a504-5097-bcd6a213921a)のメソッド、 [WorkbookPart](http://msdn.microsoft.com/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2)オブジェクト。 詳細については、次を参照してください。 [Open XML SDK 2.0](http://msdn.microsoft.com/f6a9ae68-7989-4208-97f5-3c945137a0ab)します。  
  
## <a name="bind-custom-xml-parts-to-word-content-controls"></a>カスタム XML 部分を Word コンテンツ コントロールにバインドします。  
 Word ソリューションのコンテンツ コントロールをカスタム XML 部分の要素にバインドできます。 カスタム XML 部分にコンテンツ コントロールがバインドされると、カスタム XML 部分のデータがコンテンツ コントロールのユーザー インターフェイス (UI) に表示されます。 ユーザーがコントロール内のテキストを編集すると、対応する XML 要素が自動的に更新されます。 同様に、カスタム XML 部分の要素の値が変更されると、その XML 要素にバインドされているコンテンツ コントロールに新しいデータが表示されます。 詳細については、次を参照してください。[コンテンツ コントロール](../vsto/content-controls.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメント レベルのカスタマイズにおける XML スキーマとデータ](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [方法: ドキュメント レベルのカスタマイズにカスタム XML 部分を追加します。](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [方法: VSTO アドインを使用して、カスタム XML 部分をドキュメントに追加](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [コンテンツ コントロール](../vsto/content-controls.md)   
 [チュートリアル: コンテンツ コントロールをカスタム XML 部分にバインドします。](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  