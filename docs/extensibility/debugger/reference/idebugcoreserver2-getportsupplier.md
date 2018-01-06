---
title: IDebugCoreServer2::GetPortSupplier | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2::GetPortSupplier
helpviewer_keywords: IDebugCoreServer2::GetPortSupplier
ms.assetid: acf181d4-ef42-4aa5-86f9-95fd5467ea31
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a6bd1502ad68e274880dadc195208c6174d1ab57
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver2getportsupplier"></a>IDebugCoreServer2::GetPortSupplier
Pobiera dostawcę określonego portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPortSupplier(   
   REFGUID               guidPortSupplier,  
   IDebugPortSupplier2** ppPortSupplier  
);  
```  
  
```csharp  
int GetPortSupplier(   
   ref Guid                guidPortSupplier,  
   out IDebugPortSupplier2 ppPortSupplier  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidPortSupplier`  
 [in] Identyfikator GUID dostawcy portów, które mają zostać pobrane.  
  
 `ppPortSupplier`  
 [out] Zwraca [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) obiekt reprezentujący dostawcę wybranego portu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)