---
title: IDebugApplicationThread::QueryIsDebuggerThread | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationThread.QueryIsDebuggerThread
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationThread::QueryIsDebuggerThread
ms.assetid: 78a9cfbf-7c62-4aab-82a2-35037e2f9d46
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9c3ad00fafa602b7a2f55b0412ae16c82cc2f5bf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadqueryisdebuggerthread"></a>IDebugApplicationThread::QueryIsDebuggerThread
Określa, czy ten wątek jest wątek debugera.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT QueryIsDebuggerThread();  
```  
  
#### <a name="parameters"></a>Parametry  
 Ta metoda nie przyjmuje żadnych parametrów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Metoda powiodło się i to wątek debugera.|  
|`S_FALSE`|To nie jest wątek debugera.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda określa, czy ten wątek jest wątek debugera.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)