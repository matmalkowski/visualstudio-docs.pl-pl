---
title: IDebugApplication::CreateAsyncDebugOperation | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.CreateAsyncDebugOperation
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::CreateAsyncDebugOperation
ms.assetid: bc32b101-6364-4498-8458-bd5f3ab5ad94
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8714f4401249d73cf09d241ebf4c2b2115911d6b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793813"
---
# <a name="idebugapplicationcreateasyncdebugoperation"></a>IDebugApplication::CreateAsyncDebugOperation
Udostępnia asynchroniczne operacji danego synchroniczne debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateAsyncDebugOperation(  
   IDebugSyncOperation*    psdo,  
   IDebugAsyncOperation**  ppado  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `psdo`  
 [in] Obiekt operacji synchronicznych debugowania.  
  
 `ppado`  
 [out] Obiekt operacji asynchronicznych debugowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia aparaty języka asynchronicznie obliczać wyrażeń bez jawnie synchronizacji z wątkiem debugera. Aby uzyskać więcej informacji, zobacz [interfejs IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md) i [interfejs IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [Interfejs IDebugSyncOperation](../../winscript/reference/idebugsyncoperation-interface.md)   
 [Interfejs IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)