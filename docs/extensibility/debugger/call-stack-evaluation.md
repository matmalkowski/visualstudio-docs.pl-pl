---
title: "Ocena stos wywołań | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 21626804ae60ca14b360f23acf17b3e336fa600b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="call-stack-evaluation"></a>Ocena stosu wywołań
Aby wyświetlić ramki stosu stosu wywołań w trybie przerwania, musisz zaimplementować [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) metody.  
  
## <a name="methods-for-evaluation"></a>Metody w wersji ewaluacyjnej  
 Aparat debugowania proste (DE) może być tylko jeden ramki stosu. Aby zbadać ramki stosu w trybie przerwania, musi implementować następujące metody [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Pobiera kontekst kodu dla ramki stosu. Kontekst kodu reprezentuje bieżący wskaźnik instrukcji w ramce stosu.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Pobiera kontekst dokumentu dla ramki stosu. Kontekstu dokumentu reprezentuje bieżącej lokalizacji w kodzie źródłowym dla ramki stosu. Wymagany w przypadku wyświetlanie kodu źródłowego, gdy zostały zatrzymane w programie.|  
  
 Te metody wymagają wykonania kilku interfejsów związanych z kontekstu i metod. W związku z tym należy zaimplementować [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) — metoda i z następujących metod [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Pobiera zakres instrukcji pliku kontekstu dokumentu.|  
  
 Wyliczyć kontekstów kodu, musisz zaimplementować wszystkie metody [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrola wykonywania i oceny stanu](../../extensibility/debugger/execution-control-and-state-evaluation.md)