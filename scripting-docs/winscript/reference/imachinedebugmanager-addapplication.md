---
title: IMachineDebugManager::AddApplication | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IMachineDebugManager.AddApplication
apilocation: scrobj.dll
helpviewer_keywords: IMachineDebugManager::AddApplication
ms.assetid: 7cd591b6-718c-4e77-acb7-a6dd147ddf57
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 77c31084ccc24a6bace18f009eb8372a4f68a428
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanageraddapplication"></a>IMachineDebugManager::AddApplication
Dodaje aplikację do uruchamiania liście aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AddApplication(  
   IRemoteDebugApplication*  pda,  
   DWORD*                    pdwAppCookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pda`  
 [in] Aplikacji do uruchamiania liście aplikacji.  
  
 `pdwAppCookie`  
 [out] Plik cookie jest używana do usuwania aplikacji przez Menedżera debugowania maszyny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana przez Menedżera debugowania procesu zawsze, gdy `IProcessDebugManager::AddApplication` jest wywoływana.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IMachineDebugManager](../../winscript/reference/imachinedebugmanager-interface.md)   
 [IMachineDebugManager::RemoveApplication](../../winscript/reference/imachinedebugmanager-removeapplication.md)   
 [IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)