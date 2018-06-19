---
title: IActiveScriptSiteDebug32::GetApplication | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 533d770d-06a4-4693-873e-255c9c6f0df0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
ms.openlocfilehash: bb7fdf5a6d0b380a8024cfdfa70282bcf80ba16d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793621"
---
# <a name="iactivescriptsitedebug32getapplication"></a>IActiveScriptSiteDebug32::GetApplication
Zwraca obiekt aplikacji debugowania skojarzonych z tą lokacją skryptu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppda`  
 [out] Wskaźnik do obiektu aplikacji debugowania skojarzonych z lokacją skryptu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_NOTIMPL`|Host nie obsługuje bezpośrednio debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 `GetApplication` Metody umożliwia host inteligentny do definiowania obiekt aplikacji, do którego należy każdego skryptu. Liczba aparatów skryptów powinien próbować wywołać tę metodę, aby uzyskać ich zawierającego aplikacji i odwołać się do `IProcessDebugManager::GetDefaultApplication` w przypadku niepowodzenia.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptSiteDebug32](../../winscript/reference/iactivescriptsitedebug32-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)