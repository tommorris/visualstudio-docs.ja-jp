---
title: FeatureProperties 要素 |Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- FeatureProperties element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 26fcdb1dd7fa3b62f7882deb1a077b9466e52018
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/22/2018
ms.locfileid: "36324998"
---
# <a name="featureproperties-element"></a>FeatureProperties 要素
  SharePoint に配置されるときに、機能に含まれているプロパティ値のコレクション。 フィーチャーが配置されると、プロパティ値をコードでアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```xml  
<FeatureProperties>  
  <FeatureProperty.../>  
</FeatureProperties>  
```  
  
## <a name="attributes-and-elements"></a>属性と要素
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素
  
|要素|説明|  
|-------------|-----------------|  
|[FeatureProperty](../sharepoint/featureproperty-element.md)|省略可能な要素です。<br /><br /> キー/値の形式でのカスタム プロパティを表します。|  
  
### <a name="parent-elements"></a>親要素
  
|要素|説明|  
|-------------|-----------------|  
|[ProjectItem](../sharepoint/projectitem-element.md)|SharePoint プロジェクト項目を表します。 この要素の必須のルート要素の`.spdata`ファイル。|  
  
## <a name="remarks"></a>Remarks  
 機能プロパティの詳細については、次を参照してください。[プロジェクト項目でパッケージ化と配置の情報を提供](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)します。  
  
## <a name="element-information"></a>要素情報
  
|要素|説明|  
|-------------|-----------------|  
|**名前空間**|http<nolink>://schemas.microsoft.com/VisualStudio/<br>SharePointProjectItemModel SharePointTools/2010/|  
|**スキーマ名**|SharePoint プロジェクト項目のスキーマ|  
|**ファイルの検証**|ProjectItemModelSchema.xsd|  
|**空にすることができます。**|いいえ|  
  
## <a name="see-also"></a>関連項目
 [SharePoint プロジェクト項目スキーマのリファレンス](../sharepoint/sharepoint-project-item-schema-reference.md)   
 [プロジェクト項目でパッケージ化と配置の情報を提供します。](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md)  
  
  
