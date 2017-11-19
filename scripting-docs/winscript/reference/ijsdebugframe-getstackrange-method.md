---
title: "IJsDebugFrame::GetStackRange — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cce4d4542f4f76657475636ad6d8e430e1909181
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugframegetstackrange-method"></a>IJsDebugFrame::GetStackRange — Metoda
Zwraca zakres adres bezwzględny logicznej ramki stosu JavaScript.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStart`  
 [out] Dolna większości wskaźnik stosu ramki.  
  
 `pEnd`  
 [out] Z góry większości Układarka wskaźnika ramki.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest przydatna do piecing razem śladów stosu przeplotem zebrane z wielu środowisk uruchomieniowych. Początek, wskaźniki stosu zakończenia może obejmować wiele ramek stosu komputera fizycznego (w przypadku interpretowany ramki środowiska wykonawczego języka JavaScript). Start > kończyć w miarę zwiększania się stosu wysoki niski adres.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Ijsdebugframe — interfejs](../../winscript/reference/ijsdebugframe-interface.md)