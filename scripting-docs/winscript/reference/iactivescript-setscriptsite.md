---
title: IActiveScript::SetScriptSite | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.SetScriptSite
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_SetScriptSite
ms.assetid: 47d94c32-09f8-4539-ac56-0236026f627b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 11fa9003abb03c42adcbf3a548bb5b90d763a344
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsetscriptsite"></a>IActiveScript::SetScriptSite
Informuje o aparat skryptów z [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) lokacji interfejs dostarczony przez hosta. Wywołanie tej metody przed wszystkimi innymi [IActiveScript](../../winscript/reference/iactivescript.md) służy metod interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetScriptSite(  
    IActiveScriptSite *pScriptSite  // address of host script site  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pScriptSite`  
 [in] Adres witryny hosta dostarczone skrypt ma zostać skojarzony z tym wystąpieniem aparatu skryptów. Witryny, które muszą być jednoznacznie przypisane do tego wystąpienia aparatu skryptów; Nie można udostępnić z innych aparatów skryptów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca jedną z następujących wartości:  
  
|Wartość zwracana|Znaczenie|  
|------------------|-------------|  
|`S_OK`|Powodzenie.|  
|`E_FAIL`|Wystąpił nieokreślony błąd; Nie można zakończyć inicjowanie witryny aparatu skryptów.|  
|`E_INVALIDARG`|Argument był nieprawidłowy.|  
|`E_POINTER`|Określono nieprawidłowy wskaźnik.|  
|`E_UNEXPECTED`|Nie oczekiwano wywołania (na przykład lokacji został już ustawiony).|  
  
## <a name="see-also"></a>Zobacz też  
 [IActiveScript](../../winscript/reference/iactivescript.md)