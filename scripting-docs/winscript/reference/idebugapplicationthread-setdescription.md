---
title: IDebugApplicationThread::SetDescription | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugApplicationThread.SetDescription
apilocation: pdm.dll
helpviewer_keywords: IDebugApplicationThread::SetDescription
ms.assetid: 084e5b74-af95-41b4-ae55-01f6f4d22168
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 941e2e5ac9843c8894a4dd83e23ab132620b8a02
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugapplicationthreadsetdescription"></a>IDebugApplicationThread::SetDescription
Ustawia opis tego wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetDescription(  
   LPCOLESTR  pstrDescription  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pstrDescription`  
 [in] Opis tego wątku.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda ustawia opis tego wątku.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)