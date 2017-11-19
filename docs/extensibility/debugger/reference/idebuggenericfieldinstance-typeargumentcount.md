---
title: IDebugGenericFieldInstance::TypeArgumentCount | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TypeArgumentCount
- IDebugGenericFieldInstance::TypeArgumentCount
ms.assetid: e662c5ea-a5c1-478e-a268-5980dadffcd1
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddaf2ff3323bb7e4e1da55eb1b8ad8cd8931f9c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebuggenericfieldinstancetypeargumentcount"></a>IDebugGenericFieldInstance::TypeArgumentCount
Zwraca liczbę typu argumenty parametrów dla tego wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT TypeArgumentCount(  
   ULONG32* pcArgs  
);  
```  
  
```csharp  
int TypeArgumentCount(  
   ref uint pcArgs  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcArgs`  
 [w, out] Liczba argumentów typu parametru dla tego wystąpienia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Na przykład jeśli lista\<int >, ta metoda zwraca wartość 1 oraz, jeśli lista\<int, float2 > Ta metoda zwraca wartość 2. Ta metoda zwraca wartość 0, jeśli nie wymaga argumentów typu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)