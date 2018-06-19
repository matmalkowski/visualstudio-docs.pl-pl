---
title: IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
helpviewer_keywords:
- IDebugSymbolSearchEvent2::GetSymbolSearchInfo
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 518429149ad1d997b860e486f3db4e519ef42cae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31121352"
---
# <a name="idebugsymbolsearchevent2getsymbolsearchinfo"></a>IDebugSymbolSearchEvent2::GetSymbolSearchInfo
Metoda wywoływana przez program obsługi zdarzeń, aby pobrać wyniki dotyczące proces ładowania symboli.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```csharp  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `pModule`  
 [out] Obiekt IDebugModule3 reprezentujący moduł, dla którego symbole zostały załadowane.  
  
 `pbstrDebugMessage`  
 [w, out] Zwraca ciąg zawierający komunikaty o błędach z modułu. Jeśli nie było błędu, ten ciąg będzie zawierać tylko nazwę modułu, ale nigdy nie jest pusty.  
  
> [!NOTE]
>  [C++] `pbstrDebugMessage` nie może być `NULL` i musi zostać zwolniony z `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 [out] Kombinacja flag z [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) Wyliczenie wskazujące, czy załadowano żadnych symboli.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Podczas obsługi odbiera [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) zdarzenia po podejmowana jest próba załadować symbole debugowania dla modułu, program obsługi może wywołać ta metoda ustalenie wyniki tego obciążenia.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE_INFO_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)