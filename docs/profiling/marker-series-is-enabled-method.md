---
title: marker_series::is_enabled メソッド | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c4095381fffea29e4613d42d8ecbf2d189b4cb1b
ms.sourcegitcommit: ce154aee5b403d5c1c41da42302b896ad3cf8d82
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2018
ms.locfileid: "34845120"
---
# <a name="markerseriesisenabled-method"></a>marker_series::is_enabled メソッド
任意のセッションでプロバイダーが有効にされているかどうかを調べます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `_Importance`  
 重要度レベル。  
  
 `_Category`  
 カテゴリ。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** *cvmarkersobj.h*  
  
 **名前空間:** Concurrency::diagnostic  
  
## <a name="see-also"></a>関連項目  
 [marker_series クラス](../profiling/marker-series-class.md)