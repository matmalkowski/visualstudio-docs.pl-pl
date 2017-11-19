---
title: IDebugAddress::GetAddress | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugAddress::GetAddress
helpviewer_keywords: IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ed14b69dbc116514b191aadf58d209b4d39e458
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Zwraca struktury opisujące obiekt i jego lokalizacji w jego zakresie lub kontenera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [w, out] A [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury, która jest wstawiana przez tę metodę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struktury są przekazywane do tej metody, która wypełnia je za pomocą odpowiednich informacji. Jak te informacje jest interpretowany zależy od rodzaju zwrócone informacje i procedury obsługi symboli, sam. Zobacz [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) więcej szczegółów.  
  
## <a name="see-also"></a>Zobacz też  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)