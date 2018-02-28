---
title: IDebugDocument2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 175be5f50b03573b13df8a8c0d2a9a0e1e921cc7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocument2"></a>IDebugDocument2
Ten interfejs reprezentuje dokumentu źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]zwykle implementuje ten interfejs. Aparat debugowania (DE) można też wdrożyć ten interfejs, gdy trzeba podać kod źródłowy i źródła nie istnieje na dysku.  W takich przypadkach, czy też wdrożyć DE [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) i [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) interfejsów, a także pewne dodatkowe metody na [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) i [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) interfejsów.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Metody `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, i `IDebugActivateDocumentEvent2` interfejsy zwrócić tego interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugDocument2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Pobiera nazwę dokumentu w jednym z kilku formularzy.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Pobiera identyfikator klasy dokumentu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest implementowany tylko wtedy, gdy DE dostarcza kodu źródłowego. Na przykład podczas debugowania skryptu, na stronie HTML, DE dostarcza kod źródłowy, ponieważ pobranie lub generowane dynamicznie źródła i nie istnieje jako plik dysku. Podczas debugowania tradycyjnych języków, takich jak C++, ten interfejs nie musi zostać wdrożone.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)