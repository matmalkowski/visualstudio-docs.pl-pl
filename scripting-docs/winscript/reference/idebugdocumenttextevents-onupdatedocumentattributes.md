---
title: IDebugDocumentTextEvents::onUpdateDocumentAttributes | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextEvents.onUpdateDocumentAttributes
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentTextEvents::onUpdateDocumentAttributes
ms.assetid: 48fa909c-14c2-4ca4-af86-a5809c72dd39
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef9313f612d539e3068c2dd4bb20eb5d343fc53b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttexteventsonupdatedocumentattributes"></a>IDebugDocumentTextEvents::onUpdateDocumentAttributes
Wskazuje, że atrybut dokumentu został zmieniony.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT onUpdateDocumentAttributes(  
   TEXT_DOC_ATTR  textdocattr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `textdocattr`  
 [in] Atrybuty nowego dokumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Tej metody oznacza, że zmieniono atrybuty dokumentu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [Stałe TEXT_DOC_ATTR](../../winscript/reference/text-doc-attr-constants.md)