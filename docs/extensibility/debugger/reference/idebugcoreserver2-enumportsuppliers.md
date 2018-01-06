---
title: IDebugCoreServer2::EnumPortSuppliers | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer2::EnumPortSuppliers
helpviewer_keywords: IDebugCoreServer2::EnumPortSuppliers
ms.assetid: ce0c90e4-8e02-4b08-b558-7677fb2c88f7
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e92959be7f8b55959600f6a323f96b8f8101a0ac
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugcoreserver2enumportsuppliers"></a>IDebugCoreServer2::EnumPortSuppliers
Pobiera listę wszystkich dostawców dostępnego portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumPortSuppliers(  
   IEnumDebugPortSuppliers2** ppEnum  
);  
```  
  
```csharp  
int EnumPortSuppliers(  
   out IEnumDebugPortSuppliers2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Zwraca [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) obiekt, który zawiera listę wszystkich dostawców portu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)