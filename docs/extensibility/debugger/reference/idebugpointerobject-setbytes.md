---
title: IDebugPointerObject::SetBytes | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerObject::SetBytes
helpviewer_keywords: IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91e11f0e321e286eaf669b50d2fa564fa29df314
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
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