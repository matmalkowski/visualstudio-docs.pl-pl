---
title: IDebugDocumentText2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 0c3540dc77821e6aa3fb3884d82cd0c83eee8e24
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Ten interfejs reprezentuje dokument tekstowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs, gdy jest niezbędne do dostarczania kod źródłowy w postaci tekstu. Ponieważ jest to najbardziej typową sytuacją, jeśli implementuje URZ [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interfejsu, powinien także implementować `IDebugDocumentText2` interfejsu.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Użyj `QueryInterface` metody uzyskania tego interfejsu z `IDebugDocument2` interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 Oprócz metod na `IDebugDocument2` interfejsu, tego interfejsu implementuje następujących metod:  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Pobiera rozmiar tekstu, w tym miejscu w dokumencie.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Pobiera tekst z określonej pozycji w dokumencie.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt, który implementuje ten interfejs musi implementować też <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interfejsu, który dostaw <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interfejs na potrzeby [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) obiektu.  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)