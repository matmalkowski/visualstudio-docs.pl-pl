---
title: IJsDebugFrame::Evaluate — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugFrame.Evaluate
apilocation:
- jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38e826048e85456ca63e069de67701b1fc3e9f04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24794389"
---
# <a name="ijsdebugframeevaluate-method"></a>IJsDebugFrame::Evaluate — Metoda
Ocenia wyrażenie w kontekście tej ramki stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExpressionText`  
 [in] Wyrażenie do oceny.  
  
 `ppDebugProperty`  
 [out] Obiekt reprezentujący przeglądarce właściwości.  
  
 `pError`  
 [out] Komunikat o błędzie, jeśli wystąpi błąd.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Zwraca następujące: S_OK: ocena zakończy się powodzeniem, * ppDebugProperty zawiera wynik oceny. Wartości S_FALSE: Ocena zgłasza błąd (lub operacja wersji ewaluacyjnej nie jest obsługiwana), \*pError zawiera komunikat o błędzie.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugframe — interfejs](../../winscript/reference/ijsdebugframe-interface.md)