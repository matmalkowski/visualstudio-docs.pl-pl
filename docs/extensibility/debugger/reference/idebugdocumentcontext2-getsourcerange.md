---
title: IDebugDocumentContext2::GetSourceRange | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f003ba3f97f053c4617408bfc9334da057bb98ef
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
Pobiera zakres kod źródłowy tego kontekstu dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBegPosition`  
 [w, out] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktury, która jest wypełniane pozycji początkowej. Ustaw ten argument ma wartość null, jeśli te informacje nie są potrzebne.  
  
 `pEndPosition`  
 [w, out] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) struktury, która jest wypełniane pozycję końcową. Ustaw ten argument ma wartość null, jeśli te informacje nie są potrzebne.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zakres źródła jest cały zakres kodu źródłowego z bieżącego wstecz instrukcji, aby dokładnie po poprzednich instrukcji, która kodu. Zakres źródła jest zwykle używana do mieszania instrukcje źródła, w tym komentarzy z kodu w oknie dezasemblacji.  
  
 Aby uzyskać zakres tylko instrukcji kod zawarty w kontekście tego dokumentu, należy wywołać [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)