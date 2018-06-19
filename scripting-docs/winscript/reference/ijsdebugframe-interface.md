---
title: Ijsdebugframe — interfejs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 5af46b18-9d25-4a23-b8d1-fa23bea3efcf
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f09a147375661fb52b88f531aff981897138adff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24795037"
---
# <a name="ijsdebugframe-interface"></a>IJsDebugFrame — Interfejs
Reprezentuje ramkę stosu.  
  
## <a name="syntax"></a>Składnia  
  
```  
IJsDebugFrame : public IUnknown;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[IJsDebugFrame::Evaluate — metoda](../../winscript/reference/ijsdebugframe-evaluate-method.md)|Ocenia wyrażenie w kontekście tej ramki stosu.|  
|[IJsDebugFrame::GetDebugProperty — metoda](../../winscript/reference/ijsdebugframe-getdebugproperty-method.md)|Zwraca przeglądarką właściwości dla tej ramki stosu.|  
|[IJsDebugFrame::GetDocumentPositionWithId — metoda](../../winscript/reference/ijsdebugframe-getdocumentpositionwithid-method.md)|Zwraca bieżącą pozycję tej ramki stosu w dokumencie na poziomie użytkownika.|  
|[IJsDebugFrame::GetDocumentPositionWithName — metoda](../../winscript/reference/ijsdebugframe-getdocumentpositionwithname-method.md)|Zwraca bieżącą pozycję tej ramki stosu w dokumencie na poziomie użytkownika.|  
|[IJsDebugFrame::GetName — metoda](../../winscript/reference/ijsdebugframe-getname-method.md)|Pobiera przyjazną dla użytkownika nazwę ramki stosu.|  
|[IJsDebugFrame::GetReturnAddress — metoda](../../winscript/reference/ijsdebugframe-getreturnaddress-method.md)|Pobiera adres zwrotny wypychana w chwili rozpoczęcia (zobacz GetStackRange) ramki.|  
|[IJsDebugFrame::GetStackRange — metoda](../../winscript/reference/ijsdebugframe-getstackrange-method.md)|Zwraca zakres adres bezwzględny logicznej ramki stosu JavaScript.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** jscript9diag.h  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)