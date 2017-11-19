---
title: IDebugDocumentPosition2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentPosition2
helpviewer_keywords: IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c73b7ebb1611b6688dbbe5703d5f84ac4c05b3b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Ten interfejs reprezentuje abstrakcyjne pozycji w pliku źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Visual Studio zwykle implementuje ten interfejs. Aparat debugowania (DE) również może zawierać implementację tego interfejsu, jeśli konieczne jest podanie własnej kodu źródłowego (jako po implementuje DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfejs).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest przekazywany jako argument [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Również jest podana jako część [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Unii (w szczególności [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) struktury) który z kolei jest częścią [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktury używany podczas tworzenia oczekującym punktem przerwania.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugDocumentPosition2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Pobiera nazwę pliku plik źródłowy, który zawiera ten położenie dokumentu.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Pobiera dokumentu zawierającego.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Określa, czy ta pozycja jest zawarta w danego dokumentu.|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Pobiera zakres dla tej pozycji dokumentu.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)