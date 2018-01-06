---
title: IDebugPointerObject::GetBytes | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPointerObject::GetBytes
helpviewer_keywords: IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5e07ab129cb49ffba892ba3b681e6239d4477256
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Pobiera wartość wskazywał jako serię bajtów kolejne.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetBytes(   
   DWORD  dwStart,  
   DWORD  dwCount,  
   BYTE*  pBytes,  
   DWORD* pdwBytes  
);  
```  
  
```csharp  
int GetBytes(  
   uint       dwStart,   
   uint       dwCount,   
   out byte[] pBytes,   
   out uint   pdwBytes  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwStart`  
 [in] Przesunięcie w bajtach, od początku odnosi się do obiektu.  
  
 `dwCount`  
 [in] Liczba bajtów do pobrania.  
  
 `pBytes`  
 [w, out] Tablica jest wprowadzana wartość jako serię bajtów kolejnych, zaczynając od danego przesunięcia od obiektu wskazywał.  
  
 `pdwBytes`  
 [out] Zwraca liczbę bajtów faktycznie pobrany.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana, jeśli wskaźnik reprezentowany przez to [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) wskazuje typ pierwotny lub prostego tablicę typy pierwotne (to znaczy tablicę, która może być reprezentowany przez prosty sekwencję bajtów).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)   
 [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)