---
title: IDebugFunctionPosition2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugFunctionPosition2
helpviewer_keywords: IDebugFunctionPosition2 interface
ms.assetid: a835f65b-91b0-48ad-8485-04534c814b1b
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ae7a0dd442d8a48d6c69ecfd51b2fc17a2eb2fe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugfunctionposition2"></a>IDebugFunctionPosition2
Ten interfejs reprezentuje abstrakcyjne pozycji funkcji w dokumencie źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugFunctionPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs do reprezentowania pozycja funkcję w dokumencie źródłowym.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest podana jako część [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Unii (w szczególności [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) struktury) który z kolei jest częścią [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktury, używane podczas tworzenia oczekującym punktem przerwania.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugFunctionPosition2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetFunctionName](../../../extensibility/debugger/reference/idebugfunctionposition2-getfunctionname.md)|Pobiera nazwę funkcji, która jest tej pozycji względem.|  
|[GetOffset](../../../extensibility/debugger/reference/idebugfunctionposition2-getoffset.md)|Pobiera przesunięcie od początku funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Pozycja reprezentowany przez ten interfejs jest oparty na tekst, w szczególności [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktury.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy Core](../../../extensibility/debugger/reference/core-interfaces.md)   
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)