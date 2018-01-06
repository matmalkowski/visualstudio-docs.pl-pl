---
title: IEEVisualizerService::GetCustomViewerCount | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEVisualizerService::GetCustomViewerCount
helpviewer_keywords: IEEVisualizerService::GetCustomViewerCount method
ms.assetid: f7b095c2-e538-4352-8cad-d4c6d4f6bdbc
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e1f9cf725336436e52402907fd07db094e3434db
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ieevisualizerservicegetcustomviewercount"></a>IEEVisualizerService::GetCustomViewerCount
Ta metoda pobiera liczbę dostępnych wizualizatorach typu z tej usługi.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcelt`  
 [out] Zwraca liczbę dostępnych wizualizatorach typu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) przekazuje żądanie do tej metody w jego pomocy technicznej dla wizualizatorach typu.  
  
## <a name="see-also"></a>Zobacz też  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)