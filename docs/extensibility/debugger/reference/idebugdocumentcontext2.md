---
title: IDebugDocumentContext2 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDocumentContext2
helpviewer_keywords: IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: b7184b722d0331efbfcb83e2d63563ea1ae13acc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Ten interfejs reprezentuje pozycji w pliku dokumentu źródłowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs jako część obsługę debugowania poziomu kodu źródłowego. Oprócz pozycji w kodzie źródłowym ten interfejs udostępnia metody porównanie kontekstów ani nawigować przez dokumentu kodu źródłowego.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Metody w przypadku kilku interfejsy najczęściej [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) i [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) interfejsów, zwraca ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
 W poniższej tabeli przedstawiono metody `IDebugDocumentContext2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Pobiera dokument, który zawiera ten kontekstu dokumentu.|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Pobiera nazwę zawiera dokument, który zawiera ten kontekstu dokumentu.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Pobiera listę wszystkie konteksty kod powiązany z tym kontekstem dokumentu.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Pobiera język skojarzone z tym kontekstem dokumentu.|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Pobiera zakres instrukcji pliku tego kontekstu dokumentu.|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Pobiera zakres źródłowy plik tego kontekstu dokumentu.|  
|[Porównaj](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Porównuje tego kontekstu dokumentu do danej tablicy kontekstów dokumentu.|  
|[Wyszukiwanie](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Przenosi kontekstu dokumentu przez daną liczbę instrukcji lub wierszy.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Zestaw: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)