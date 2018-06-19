---
title: BP_LOCATION_DATA_STRING | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- BP_LOCATION_DATA_STRING
helpviewer_keywords:
- BP_LOCATION_DATA_STRING structure
ms.assetid: 445d6f3f-95b0-47ac-85e2-51b778240687
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ae83bf4d0f8ba6435a962f5c1477e460d69ae27f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31100601"
---
# <a name="bplocationdatastring"></a>BP_LOCATION_DATA_STRING
Używana do ustawiania punkty przerwania danych, które są oparte na ciąg, który użytkownik może wprowadzić z zintegrowane środowisko programistyczne (IDE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _BP_LOCATION_DATA_STRING {   
   IDebugThread2* pThread;  
   BSTR           bstrContext;  
   BSTR           bstrDataExpr;  
   DWORD          dwNumElements;  
} BP_LOCATION_DATA_STRING;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) obiekt, który reprezentuje wątku, w którym występuje punktu przerwania.  
  
 `bstrContext`  
 Kontekst punktu przerwania w kodzie, zwykle nazwę metody lub funkcji wyświetlanego w stosie wywołań.  
  
 `bstrDataExpr`  
 Ciąg danych, które użytkownik wprowadza można ustawić punktu przerwania.  
  
 `dwNumElements`  
 Liczba elementów w ciągu danych, w którym występuje punktu przerwania.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest elementem członkowskim [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktury jako część Unii.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)