---
title: IDebugPortSupplier2::CanAddPort | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier2::CanAddPort
helpviewer_keywords: IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 6b493229ab33f628c54580711604b16a4e2b5c5b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Sprawdza, czy dostawca portu można dodawać nowych portów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli port można dodać, zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` wskazująca portów nie można dodać do tego portu dostawcy.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej metody przed wywołaniem [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) metody, ponieważ to drugie metoda tworzy portu, a także dodawanie, który może być czasochłonna operacja.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)