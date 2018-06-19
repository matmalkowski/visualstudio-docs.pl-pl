---
title: IDebugMemoryContext2::Subtract | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c6cc7265def2d1a4b184f27865461706e62b98f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113640"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Odejmuje określoną wartość z bieżącego kontekstu i zwraca nowy kontekst.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCount`  
 [in] Liczba bajtów pamięci, aby zmniejszyć.  
  
 `ppMemCxt`  
 [out] Zwraca nowy [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kontekst pamięci jest adresem, więc odjęcie wartości z adresu tworzy nowy adres, który wymaga nowy interfejs kontekstu.  
  
 Ta metoda zawsze musi mieć nowy kontekst, nawet jeśli adres wynikowa znajduje się poza obszar pamięci skojarzone z tym kontekstem. Jedynym wyjątkiem jest, jeśli w nowym kontekście można przydzielić pamięć lub `ppMemCxt` jest wartość null (która jest błąd).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)