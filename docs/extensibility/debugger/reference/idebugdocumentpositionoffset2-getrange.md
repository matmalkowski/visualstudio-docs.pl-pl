---
title: IDebugDocumentPositionOffset2::GetRange | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 60d7ee73be7ccd421c7f5e0b4861e9cd935fbdb0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109756"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
Pobiera zakres dla bieżącego położenia dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwBegOffset`  
 [w, out] Przesunięcie dla pozycja początkowa zakresu. Ustaw ten parametr ma wartość null, jeśli te informacje nie są potrzebne.  
  
 `pdwEndOffset`  
 [w, out] Przesunięcie dla pozycja końcowa zakresu. Ustaw ten parametr ma wartość null, jeśli te informacje nie są potrzebne.  
  
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
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)