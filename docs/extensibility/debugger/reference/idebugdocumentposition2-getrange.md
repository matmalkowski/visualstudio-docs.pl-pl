---
title: IDebugDocumentPosition2::GetRange | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d4a80bebba1000c73af2d7e2cfd05e67fa44b1b7
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109204"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
Pobiera zakres dla tej pozycji dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetRange(   
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
 Zakres określony w stanie dokumentu lokalizacji punktu przerwania jest używany przez aparat debugowania (DE) do przodu wyszukiwania instrukcję, która faktycznie wspiera kodu. Rozważmy na przykład następujący kod:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Wiersz 5 przyczynia się żaden kod do debugowanego programu. Jeśli debugera, która ustawia punkt przerwania w wierszu 5 chce DE wyszukiwania do przodu określonym dla pierwszego wiersza, która wspiera kodu, debuger określić zakres zawierający punkt przerwania może prawidłowo rozmieszczenia wierszy dodatkowe kandydata. Niemcy będzie następnie wyszukuj do przodu za pośrednictwem tych wierszy aż do znalezienia go wiersza, który może zaakceptować punktu przerwania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)