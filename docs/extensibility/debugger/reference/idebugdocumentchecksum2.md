---
title: IDebugDocumentChecksum2 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentChecksum2 interface
ms.assetid: 6d22fa94-21aa-46cb-b5b5-32a6399ebb20
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 068447399a8cfd43cb5fe07ea82e7cf4400f460c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106721"
---
# <a name="idebugdocumentchecksum2"></a>IDebugDocumentChecksum2
Reprezentuje sumy kontrolnej dla dokumentu debugowania i umożliwia przekazywanie sumy kontrolnej między składnikami.  
  
## <a name="syntax"></a>Składnia  
  
```  
IDebugDocumentChecksum2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Uwagi dotyczące implementacji  
 Ten interfejs może być zaimplementowany przez każdego składnika, który ujawnia [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfejsu. Jednak jest głównie stosowana przez aparaty debugowania, aby suma kontrolna osadzone w pliku symboli (*.pdb) może być przekazywane z powrotem do środowiska IDE i używana przy wyszukiwaniu źródła.  
  
## <a name="methods"></a>Metody  
 W poniższej tabeli przedstawiono metody `IDebugDocumentChecksum2`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetChecksumAndAlgorithmId](../../../extensibility/debugger/reference/idebugdocumentchecksum2-getchecksumandalgorithmid.md)|Pobiera identyfikator sumy kontrolnej i algorytm dokumentu podana maksymalna liczba bajtów do użycia.|  
  
## <a name="requirements"></a>Wymagania  
 Nagłówek: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll