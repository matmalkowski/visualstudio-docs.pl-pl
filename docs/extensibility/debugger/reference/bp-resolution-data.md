---
title: BP_RESOLUTION_DATA | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: BP_RESOLUTION_DATA
helpviewer_keywords: BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 34ccdd131592896bb243d6d15a3cc148f16c9c14
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bpresolutiondata"></a>BP_RESOLUTION_DATA
Przedstawia wynik powiązanie punktu przerwania danych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct _BP_RESOLUTION_DATA {   
   BSTR              bstrDataExpr;  
   BSTR              bstrFunc;  
   BSTR              bstrImage;  
   BP_RES_DATA_FLAGS dwFlags;  
} BP_RESOLUTION_DATA;  
```  
  
```csharp  
public struct BP_RESOLUTION_DATA {   
   public string bstrDataExpr;  
   public string bstrFunc;  
   public string bstrImage;  
   public uint   dwFlags;  
};  
```  
  
## <a name="members"></a>Elementy członkowskie  
 `bstrDataExpr`  
 Wyrażenie danych, która została powiązana.  
  
 `bstrFunc`  
 Nazwa funkcji punktu przerwania danych została powiązana w (jeśli istnieje).  
  
 `bstrImage`  
 Nazwa modułu (na przykład MyModule.dll) powiązanej w punktu przerwania danych.  
  
 `dwFlags`  
 Wartość z zakresu od [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md) wyliczenie opisujące jak punktu przerwania danych jest zaimplementowana.  
  
## <a name="remarks"></a>Uwagi  
 Ta struktura jest elementem członkowskim [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) struktury, która jest w włączyć członkiem [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) zwrócony przez strukturę [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)metody.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury i Unii](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)