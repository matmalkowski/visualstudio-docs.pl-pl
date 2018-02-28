---
title: IDebugDocumentText::GetPositionOfContext | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugDocumentText.GetPositionOfContext
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetPositionOfContext
ms.assetid: 90fec730-c3fb-45fb-92ef-05ecc90dca38
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f843d71096dea4c22eda757a4d6975dfda94180
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextgetpositionofcontext"></a>IDebugDocumentText::GetPositionOfContext
Zwraca zakres pozycji znaku odpowiadający kontekstu dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetPositionOfContext(  
   IDebugDocumentContext*  psc,  
   ULONG*                  pcCharacterPosition,  
   ULONG*                  cNumChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psc`  
 [in] Obiekt kontekstu dokumentu.  
  
 `pcCharacterPosition`  
 [out] Uruchom lokalizacji pozycji znaku zakresu.  
  
 `cNumChars`  
 [out] Liczba znaków w zakresie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Kontekstu dokumentu przekazane do tej metody musi być skojarzony z tym dokumentem.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugDocumentText](../../winscript/reference/idebugdocumenttext-interface.md)