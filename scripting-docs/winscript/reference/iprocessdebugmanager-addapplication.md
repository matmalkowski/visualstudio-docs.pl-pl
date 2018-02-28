---
title: IProcessDebugManager::AddApplication | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IProcessDebugManager.AddApplication
apilocation:
- pdm.dll
helpviewer_keywords:
- IProcessDebugManager::AddApplication
ms.assetid: 73828299-11eb-4c58-ad70-f80f2d0eede8
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a221aa0038b0b3fd5046b9ada08e2de86f33a895
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iprocessdebugmanageraddapplication"></a>IProcessDebugManager::AddApplication
Dodaje aplikację do listy Menedżera debugowania maszyny uruchomionych aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AddApplication(  
   IDebugApplication*  pda,  
   DWORD*              pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 [in] Debugowanie aplikacji można dodać do listy uruchomionych aplikacji.  
  
 `pdwAppCookie`  
 [out] Plik cookie jest używana do usuwania aplikacji przez Menedżera debugowania maszyny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda dodaje aplikację do uruchamiania liście aplikacji w Menedżerze debugowania maszyny.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IProcessDebugManager](../../winscript/reference/iprocessdebugmanager-interface.md)   
 [IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)