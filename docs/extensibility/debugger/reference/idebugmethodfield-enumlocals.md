---
title: IDebugMethodField::EnumLocals | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::EnumLocals
helpviewer_keywords: IDebugMethodField::EnumLocals method
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: aa4ab5a8963ae8364e35cdc0e2a5237a75d35994
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmethodfieldenumlocals"></a>IDebugMethodField::EnumLocals
Tworzy moduł wyliczający dla wybranych zmiennych lokalnych metody.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiekt reprezentujący adres debugowania, który wybiera kontekstu lub z którego można pobrać ustawień regionalnych.  
  
 `ppLocals`  
 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę zmiennych lokalnych; w przeciwnym razie zwraca wartość null, jeśli nie ma żadnych zmiennych lokalnych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartości S_FALSE, jeśli nie ma żadnych zmiennych lokalnych. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wyliczane są tylko zmienne zdefiniowane w bloku, zawierający adres danego debugowania. Jeśli potrzebne są wszystkie zmienne lokalne, w tym zmienne lokalne generowane przez kompilator, wywołaj [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) metody.  
  
 Metoda może zawierać wielu kontekstów lub bloków zakresu. Na przykład następująca metoda contrived zawiera trzy zakresy, dwa bloki wewnętrzny i treści metody, sama.  
  
```csharp  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) obiekt reprezentuje `func` metody. Wywoływanie `EnumLocals` metody z [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) ustawioną `Inner Scope 1` adres zwraca wyliczenie zawierający `temp1` zmiennej, na przykład.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)