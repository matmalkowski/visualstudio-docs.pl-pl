---
title: "IJsDebugFrame::GetDocumentPositionWithName — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49afb5903e190280d226a24b22dc389041861c52
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetdocumentpositionwithname-method"></a>IJsDebugFrame::GetDocumentPositionWithName — Metoda
Zwraca bieżącą pozycję tej ramki stosu w dokumencie na poziomie użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDocumentName`  
 [out] W przypadku skryptów statyczny adres URL dokumentu. Skryptów dynamicznych zwracana jest nazwa zawierający typ skryptu (na przykład eval kodu, funkcja kodu itp.).  
  
 `pLine`  
 [out] 1 na podstawie pozycji w dokumencie.  
  
 `pColumn`  
 [out] 1 na podstawie pozycji w dokumencie.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugframe — interfejs](../../winscript/reference/ijsdebugframe-interface.md)