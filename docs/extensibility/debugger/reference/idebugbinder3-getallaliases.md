---
title: IDebugBinder3::GetAllAliases | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6da1b26b41c80d0417da16f478ef3f6672edd12a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099398"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Ta metoda pobiera listę aliasów z programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `uRequest`  
 [in] Maksymalną liczbę aliasów do zwrócenia (określa długość tablicy przekazany `ppAliases`).  
  
 `ppAliases`  
 [w, out] Tablica do wypełnienia się przy użyciu aliasy (jeśli jest to wartość null i `uRequest` wynosi 0, liczba aliasy, które mogą być zwrócone zostaną zwrócone przez `puFetched`).  
  
 `puFetched`  
 [out] Zwraca liczbę aliasów uzyskany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)