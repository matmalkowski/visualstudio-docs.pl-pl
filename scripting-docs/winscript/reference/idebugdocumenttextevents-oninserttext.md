---
title: IDebugDocumentTextEvents::onInsertText | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentTextEvents.onInsertText
apilocation: scrobj.dll
helpviewer_keywords: IDebugDocumentTextEvents::onInsertText
ms.assetid: 775881de-497a-47a9-86ab-823d77745a72
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a00adb996711dc6364edd44babf0c3cde1595947
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttexteventsoninserttext"></a>IDebugDocumentTextEvents::onInsertText
Wskazuje, czy nowy tekst został dodany do dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT onInsertText(  
   ULONG  cCharacterPosition,  
   ULONG  cNumToInsert  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 [in] Pozycja znaku, gdzie dodano nowego tekstu.  
  
 `cNumToInsert`  
 [in] Liczba znaków, które zostały wstawione.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest zazwyczaj wywoływana przez hosta, który ładuje stopniowo zawartości, takich jak przeglądarki sieci Web.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentTextEvents](../../winscript/reference/idebugdocumenttextevents-interface.md)   
 [IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)