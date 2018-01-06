---
title: BP_LOCATION_CODE_ADDRESS | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_LOCATION_CODE_ADDRESS
helpviewer_keywords: BP_LOCATION_CODE_ADDRESS structure
ms.assetid: 83c9da8b-19d9-4be5-b225-854543654901
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 0c7c2378fd9735f097bf0762cf41804862041db9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bplocationcodeaddress"></a>BP_LOCATION_CODE_ADDRESS
Określa lokalizację punktu przerwania pod adresem w kodzie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _BP_LOCATION_CODE_ADDRESS {   
   BSTR bstrContext;  
   BSTR bstrModuleUrl;  
   BSTR bstrFunction;  
   BSTR bstrAddress;  
} BP_LOCATION_CODE_ADDRESS;  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `bstrContext`  
 Kontekst punktu przerwania, zazwyczaj nazwę metody lub funkcji wyświetlanego w stosie wywołań.  
  
 `bstrModuleUrl`  
 Adres URL moduł, który zawiera punkt przerwania.  
  
 `bstrFunction`  
 Nazwa funkcji, która zawiera punkt przerwania.  
  
 `bstrAddress`  
 Adres punktu przerwania, która jest analizowana przez ewaluatora wyrażenia, aby powiązać go do [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest elementem członkowskim [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) struktury jako część Unii.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)