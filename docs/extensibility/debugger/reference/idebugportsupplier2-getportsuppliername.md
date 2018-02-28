---
title: IDebugPortSupplier2::GetPortSupplierName | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugPortSupplier2::GetPortSupplierName
helpviewer_keywords:
- IDebugPortSupplier2::GetPortSupplierName
ms.assetid: e4c368ab-640d-4b5b-9f74-810dc9364d8f
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0104a791ae3f523db7afa83e92f9a2714984c08a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier2getportsuppliername"></a>IDebugPortSupplier2::GetPortSupplierName
Pobiera nazwę dostawcy portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetPortSupplierName(   
   BSTR* pbstrName  
);  
```  
  
```csharp  
int GetPortSupplierName(   
   out string pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrName`  
 [out] Zwraca nazwę dostawcy portu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)