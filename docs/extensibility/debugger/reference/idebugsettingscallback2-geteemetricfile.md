---
title: IDebugSettingsCallback2::GetEEMetricFile | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricFile
ms.assetid: 3a0bf9e5-bbd2-4d15-840d-8244732787fc
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b3feefc8b123574d4a3b475b6065cd922faef9eb
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsettingscallback2geteemetricfile"></a>IDebugSettingsCallback2::GetEEMetricFile
Pobiera plik metryki ewaluatora wyrażenia, daną nazwę lub metryki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetEEMetricFile(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   BSTR*   pbstrValue  
);  
```  
  
```csharp  
private int GetEEMetricFile(  
   ref Guid   guidLang,  
   ref Guid   guidVendor,  
   string     pszMetric,  
   out string pbstrValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidLang`  
 [in] Unikatowy identyfikator języka programowania.  
  
 `guidVendor`  
 [in] Unikatowy identyfikator dostawcy.  
  
 `pszMetric`  
 [in] Nazwa metryki.  
  
 `pbstrValue`  
 [out] Zwraca zawartość pliku metryki jako ciąg.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)