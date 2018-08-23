---
title: IDebugDocumentPosition2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d240388ee1331e8dbdb2148f58f7a761ddde7a83
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42680557"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugDocumentPosition2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentposition2).  
  
Ten interfejs stanowi abstrakcyjną pozycji w pliku źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Program Visual Studio zazwyczaj implementują ten interfejs. Aparat debugowania (DE) będzie także implementować ten interfejs, jeśli konieczne jest podanie własnego kodu źródłowego (jako po implementuje DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfejsu).  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Ten interfejs jest przekazywany jako argument do [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Również jest dostarczany jako część [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Unii (w szczególności [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) struktury) który z kolei jest częścią [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) struktury który jest używany podczas tworzenia oczekujący punkt przerwania.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugDocumentPosition2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Pobiera nazwę pliku pliku źródłowego, który zawiera położenie tego dokumentu.|  
|[Getdocument —](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Pobiera dokumentu zawierającego.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Określa, jeśli ta pozycja jest zawarty w danym dokumencie.|  
|[Getrange —](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Pobiera zakres dla tej pozycji dokumentu.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)

