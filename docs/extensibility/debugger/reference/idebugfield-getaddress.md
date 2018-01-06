---
title: IDebugField::GetAddress | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetAddress
helpviewer_keywords: IDebugField::GetAddress method
ms.assetid: 6981bf03-66ef-4bf9-87ea-f6c9624486cb
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c7f8c4c218098aae09743617ce7e0798b59849c0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfieldgetaddress"></a>IDebugField::GetAddress
Ta metoda pobiera adres debugowania pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAddress(   
   IDebugAddress** ppAddress  
);  
```  
  
```csharp  
int GetAddress(  
   out IDebugAddress ppAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppAddress`  
 [out] Zwraca adres jako [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)