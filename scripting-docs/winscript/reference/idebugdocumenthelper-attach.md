---
title: IDebugDocumentHelper::Attach | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentHelper.Attach
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentHelper::Attach
ms.assetid: 834f23a9-716d-44df-b23c-d1bf6da60e79
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 97ddb49f61e9df4044eb6e16b853e6cf8155162a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenthelperattach"></a>IDebugDocumentHelper::Attach
Dodaje ten dokument w drzewie dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Attach(  
   IDebugDocumentHelper*  pddhParent  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pddhParent`  
 [in] Drzewo dokumentu, gdzie ma zostać dodana tego dokumentu. Może mieć wartości NULL.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda dodaje ten dokument do dokumentu drzewa, za pomocą `pddhParent` jako element nadrzędny. Jeśli `pddhParent` jest `NULL`, dokument będzie dokumentów najwyższego poziomu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentHelper::Detach](../../winscript/reference/idebugdocumenthelper-detach.md)   
 [Interfejs IDebugDocumentHelper](../../winscript/reference/idebugdocumenthelper-interface.md)