---
title: IDebugDocumentContext2 | Dokumentacja firmy Microsoft
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
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9051790d0db88002a23905cf7ae6320a140e5869
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42676733"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [IDebugDocumentContext2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdocumentcontext2).  
  
Ten interfejs reprezentuje pozycji w dokumencie pliku źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Aparat debugowania (DE) implementuje ten interfejs jako część obsługę debugowania poziomu kodu źródłowego. Oprócz pozycji w kodzie źródłowym ten interfejs dostarcza metody do porównywania kontekstów ani nawigować przez dokumentu kodu źródłowego.  
  
## <a name="notes-for-callers"></a>Uwagi dotyczące wywoływania  
 Metody na kilka interfejsów najczęściej [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) i [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) interfejsów, zwraca ten interfejs.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
 W poniższej tabeli przedstawiono metody `IDebugDocumentContext2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Getdocument —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Pobiera dokument, który zawiera ten kontekst dokumentu.|  
|[Getname —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Pobiera nazwę zawiera dokument, który zawiera ten kontekst dokumentu.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Pobiera listę wszystkich kontekstach kodu skojarzone z tym kontekstem dokumentu.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Pobiera język skojarzone z tym kontekstem dokumentu.|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Pobiera zakres instrukcji pliku tego kontekstu dokumentu.|  
|[Getsourcerange —](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Pobiera zakres źródłowy plik tego kontekstu dokumentu.|  
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Porównuje ten kontekst dokumentu do danej tablicy kontekstów dokumentu.|  
|[Wyszukiwanie](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Przenosi kontekstu dokumentu o podanej liczbie wierszy lub instrukcji.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Zobacz też  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)

