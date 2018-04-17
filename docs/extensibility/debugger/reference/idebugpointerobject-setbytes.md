---
title: IDebugPointerObject::SetBytes | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a8234117d7965c4f2e471855d39ed0c3cee1f88c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Ustawia wartość wskazywał z szeregu kolejnych bajtów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int SetBytes(  
   uint     dwStart,   
   uint     dwCount,   
   byte[]   pBytes,   
   out uint pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwStart`  
 [in] Przesunięcie w bajtach, od początku odnosi się do obiektu.  
  
 `dwCount`  
 [in] Liczba bajtów do ustawienia.  
  
 `pBytes`  
 [in] Tablica bajtów reprezentujący nową wartość. Ta wartość jest przechowywana do obiektu, zaczynając od danego przesunięcia.  
  
 `pdwBytes`  
 [out] Zwraca liczbę bajtów faktycznie ustawić.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana, jeśli wskaźnik reprezentowany przez to [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) wskazuje typ pierwotny lub prostego tablicę typy pierwotne (to znaczy tablicę, która może być reprezentowany przez prosty sekwencję bajtów). To `IDebugPointerObject` obiekt nie może być odwołanie o wartości null (go musi wskazywać adres w pamięci).  
  
## <a name="see-also"></a>Zobacz też  
 [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)   
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)