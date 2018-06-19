---
title: IJsDebugFrame::GetDocumentPositionWithId — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.GetDocumentPositionWithId
apilocation:
- jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f11e9ad51094522adec99ef82681f42ac500a251
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794473"
---
# <a name="ijsdebugframegetdocumentpositionwithid-method"></a>IJsDebugFrame::GetDocumentPositionWithId — Metoda
Zwraca bieżącą pozycję tej ramki stosu w dokumencie na poziomie użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDocumentId`  
 [out] Unikatowy identyfikator dla dokumentu źródłowego (wskaźnik do IDebugDocumentText).  
  
 `pCharacterOffset`  
 [out] Przesunięcie znaku liczony od zera na początku skryptu.  
  
 `pStatementCharCount`  
 [out] Długość bieżącej instrukcji, która rozpoczyna się od * pCharacterOffset w znakach.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugframe — interfejs](../../winscript/reference/ijsdebugframe-interface.md)