---
title: IDebugCoreServer2::GetMachineInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2::GetInfo
helpviewer_keywords: IDebugCoreServer2::GetInfo
ms.assetid: 8fa1a1d3-9fcb-4fb3-bf4e-e7172ac08d77
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 449a8c0ce9bd7ac71ed0ba13b8c46274b7e5889b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver2getmachineinfo"></a>IDebugCoreServer2::GetMachineInfo
Pobiera opis komputerze, na którym pracuje core server.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetInfo(   
   MACHINE_INFO_FIELDS Fields,  
   MACHINE_INFO*       pMachineInfo  
);  
```  
  
```csharp  
int GetInfo(   
   enum_ MACHINE_INFO_FIELDS  Fields,  
   MACHINE_INFO[]             pMachineInfo  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Fields`  
 [in] Kombinacja flag z [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) wyliczenie określające, które pola `pMachineInfo` mają zostać wypełnione.  
  
 `pMachineInfo`  
 [w, out] A [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) struktury, która jest wypełniane opis maszyny.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)   
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)