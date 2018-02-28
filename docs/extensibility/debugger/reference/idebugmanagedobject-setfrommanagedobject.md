---
title: IDebugManagedObject::SetFromManagedObject | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: da0526c060175a6e00a7b45a7ef2e347dba0d89e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Ustawia wartość wystąpienia obiektu klasy wartości z wystąpienia klasy wartości podać jako parametr.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pManagedObject`  
 [in] Interfejs, który reprezentuje zarządzanego obiektu zawierającego nowe wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda służy do zmiany obiektu zarządzanego reprezentowany przez [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)