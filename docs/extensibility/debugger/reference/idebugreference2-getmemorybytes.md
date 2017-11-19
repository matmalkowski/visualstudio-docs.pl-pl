---
title: IDebugReference2::GetMemoryBytes | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2::GetMemoryBytes
helpviewer_keywords: IDebugReference2::GetMemoryBytes
ms.assetid: 2006cb2b-1dfa-4a2d-8e3e-db2ce0302e0d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a7ec9dc451957d886fdc8a1655334ca5831c6bd1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugreference2getmemorybytes"></a>IDebugReference2::GetMemoryBytes
Pobiera liczbę bajtów pamięci, które fizycznie zawiera wartości odwołania. Zarezerwowane do użytku w przyszłości.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMemoryBytes (   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes (   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppMemoryBytes`  
 [out] Zwraca [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) obiektu, który może służyć do pobierania pamięci, która zawiera wartość odwołania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zawsze zwraca `E_NOTIMPL`.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)