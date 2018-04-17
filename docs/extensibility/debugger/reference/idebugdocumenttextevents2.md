---
title: IDebugDocumentTextEvents2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentTextEvents2
helpviewer_keywords:
- IDebugDocumentTextEvents2 interface
ms.assetid: a10cbb6b-11a8-4056-b42a-2ecebf0e690d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0f34bb09847659fdfc1dfcbd036aef2a47c8bd5b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumenttextevents2"></a>IDebugDocumentTextEvents2
Ten interfejs jest używana do powiadamiania o zmianach w dokumencie źródłowym, które są dostarczane przez aparat debugowania programu Visual Studio.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocumentTextEvents2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Niemcy implementuje ten interfejs obsługuje wprowadzania zmian do kodu źródłowego. Ten interfejs jest zwykle implementowany na ten sam obiekt, który implementuje [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uzyskuje ten interfejs poprzez wywołanie <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> metody. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> Interfejsu są uzyskiwane z wywołania <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.EnumConnectionPoints%2A> metody. <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> Interfejsu uzyskuje się poprzez wywołanie [QueryInterface](/cpp/atl/queryinterface) metoda [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugDocumentTextEvents2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[OnDestroy](../../../extensibility/debugger/reference/idebugdocumenttextevents2-ondestroy.md)|Wskazuje, czy cały dokument został zlikwidowany.|  
|[onInsertText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-oninserttext.md)|Powiadamia pakietu debugowania wstawiony tekstu do dokumentu.|  
|[onRemoveText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onremovetext.md)|Powiadamia pakietu debugowania, że tekst został usunięty z dokumentu.|  
|[onReplaceText](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onreplacetext.md)|Powiadamia pakietu debugowania, że tekst został zastąpiony w dokumencie.|  
|[onUpdateTextAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatetextattributes.md)|Powiadamia pakietu debugowania atrybutów tekstu zostały zaktualizowane w dokumencie.|  
|[onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)|Powiadamia odbiornik zdarzenia zaktualizowano atrybuty dokumentu.|  
  
## <a name="remarks"></a>Uwagi  
 Tylko aparaty debugowania, które dostarczają swoich własnych dokumentów będzie korzystać z `IDebugDocumentTextEvent2` interfejsu. Przykładem tego może być aparat debugowania skryptów. Właśnie interpretowanie skrypty, nowy kod źródłowy mogą być generowane nie ma w żadnym pliku dysku, który jest znany tylko DE.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)