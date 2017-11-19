---
title: IActiveScriptSite::OnScriptError | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptSite.OnScriptError
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptSite_OnScriptError
ms.assetid: 5c9c85cc-21ad-4232-be83-a24cc7570108
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ae066fe7fa04a5c97dec618c65ccee3f90984a0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsiteonscripterror"></a>IActiveScriptSite::OnScriptError
Informuje hosta, że wystąpił błąd wykonywania w trakcie aparat skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OnScriptError(  
    IActiveScriptError *pase  // address of error interface  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pase`  
 [in] Adres obiektu błąd [IActiveScriptError](../../winscript/reference/iactivescripterror.md) interfejsu. Hosta można użyć tego interfejsu do uzyskiwania informacji o błąd wykonywania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca `S_OK` Jeśli błąd został prawidłowo obsłużony lub OLE zdefiniowane w przeciwnym razie kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)