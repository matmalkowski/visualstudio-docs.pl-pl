---
title: IDebugApplication::Close | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplication.Close
apilocation: pdm.dll
helpviewer_keywords: IDebugApplication::Close
ms.assetid: d19baa07-3f3b-47de-8185-5eb3e7ac8b46
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8a17301842cefac7c7f257a4bc0e437670e28064
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationclose"></a>IDebugApplication::Close
Powoduje, że tej aplikacji zwolnić wszystkie odwołania, a następnie wprowadź nieaktywny.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Close();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Zwykle właściciel aplikacji wywołuje tę metodę, gdy aplikacja jest kończona.  
  
 Ta metoda powoduje `IApplicationDebugger::onClose` do wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onClose](../../winscript/reference/iapplicationdebugger-onclose.md)