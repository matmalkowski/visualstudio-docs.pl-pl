---
title: IDebugDocumentHelper::SetDefaultTextAttr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.SetDefaultTextAttr
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::SetDefaultTextAttr
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49b6da490e1eefe13ae21a9875952032585372f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelpersetdefaulttextattr"></a>IDebugDocumentHelper::SetDefaultTextAttr
Ustawia domyślne atrybuty dla tekstu, który nie znajduje się w bloku skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `staTextAttr`  
 Atrybuty tekstu źródłowego domyślne.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 O ile domyślne atrybuty zostaną zmienione przez tę metodę, domyślne atrybuty dla tekstu poza blokiem skryptu jest SOURCETEXT_ATTR_NONSOURCE. Interfejsu użytkownika można użyć tych informacji do oznaczania tekstu poza blokach skryptu jako tylko do odczytu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [Wyliczenie SOURCE_TEXT_ATTR](../../winscript/reference/source-text-attr-enumeration.md)