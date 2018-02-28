---
title: IDebugApplicationThread::QueryIsCurrentThread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugApplicationThread.QueryIsCurrentThread
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplicationThread::QueryIsCurrentThread
ms.assetid: 1580d3aa-3be8-4779-ac7b-41ab5c9edede
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a291005a7c5b85230c55c736c68de82c0290d0e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadqueryiscurrentthread"></a>IDebugApplicationThread::QueryIsCurrentThread
Określa, czy ten wątek jest aktualnie uruchomiony.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QueryIsCurrentThread();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Metoda zakończyło się pomyślnie i jest aktualnie uruchomiony.|  
|`S_FALSE`|To nie jest aktualnie uruchomiony.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, czy ten wątek jest aktualnie uruchomiony.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)