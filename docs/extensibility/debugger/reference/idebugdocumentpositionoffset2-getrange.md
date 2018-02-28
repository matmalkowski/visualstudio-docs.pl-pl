---
title: IDebugDocumentPositionOffset2::GetRange | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 09b415e01b6c768f471bdf9ad2e595d1a910d582
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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