---
title: IDebugAsyncOperation::GetResult | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60181904408010f35fa4d99d182216e665583aab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
Udostępnia wartość zwrotna i parametr obiektu zwracanego przez operację debugowania synchronicznego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `phrResult`  
 [out] Jeśli operacja została zakończona, `phrResult` jest zwracana wartość `IDebugSyncOperation::Execute`.  
  
 `ppunkResult`  
 [out] Jeśli operacja została zakończona, `ppunkResult` jest parametr obiektu zwrócony przez operację.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
|`E_PENDING`|Operacja nie została ukończona.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli operacja została zakończona, ta metoda zwraca `HRESULT` i parametru z obiektu `IDebugSyncOperation::Execute`.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugAsyncOperation](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)