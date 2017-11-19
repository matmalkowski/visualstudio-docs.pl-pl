---
title: IDebugDocumentContext::EnumCodeContexts | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugDocumentContext.EnumCodeContexts
apilocation: pdm.dll
helpviewer_keywords: IDebugDocumentContext::EnumCodeContexts
ms.assetid: fb0aa64e-c458-4ef1-bcd8-5cebdc972549
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 300102d75fcfa797e8e073b9a1ce77cc5ee2827a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentcontextenumcodecontexts"></a>IDebugDocumentContext::EnumCodeContexts
Wylicza kontekstów kod powiązany z tym kontekstem dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumCodeContexts(  
   IEnumDebugCodeContexts**  ppescc  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppescc`  
 [out] Konteksty kod powiązany z tym kontekstem dokumentu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Dokument jest zazwyczaj skojarzony z kontekstem tylko jeden kod, chyba że dokument jest dołączanego pliku lub szablonu.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentContext](../../winscript/reference/idebugdocumentcontext-interface.md)