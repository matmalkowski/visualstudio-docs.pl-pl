---
title: IDebugField::GetExtendedInfo | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugField::GetExtendedInfo
helpviewer_keywords: IDebugField::GetExtendedInfo method
ms.assetid: 46c0dd4d-4fd5-4efd-a908-71e4248e8e8d
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a5b52c5634b4b34edf11ddb8a56317cc237063bf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfieldgetextendedinfo"></a>IDebugField::GetExtendedInfo
Ta metoda pobiera rozszerzone informacje dotyczące pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetExtendedInfo(   
   REFGUID guidExtendedInfo,  
   BYTE**  prgBuffer,  
   DWORD*  pdwLen  
);  
```  
  
```csharp  
int GetExtendedInfo(  
   ref Guid guidExtendedInfo,   
   IntPtr[] prgBuffer,   
   ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidExtendedInfo`  
 [in] Wybiera informacje, które mają zostać zwrócone. Prawidłowe wartości to:  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`guidConstantValue`|Wartość sekwencję bajtów.|  
|`guidConstantType`|Typu jako typu.|  
  
 `prgBuffer`  
 [out] Zwraca rozszerzonych informacji.  
  
 `pdwLen`  
 [w, out] Zwraca rozmiar danych rozszerzonych w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Obecnie ta metoda zwraca tylko typu lub wartości stałej. Obiekt wywołujący musi wolnego buforu zwracane w `prgBuffer` przez wywołanie modelu COM `CoTaskMemFree` — funkcja (C++) lub <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> (C#).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)