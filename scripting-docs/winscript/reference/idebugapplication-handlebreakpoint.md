---
title: IDebugApplication::HandleBreakPoint | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugApplication.HandleBreakPoint
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugApplication::HandleBreakPoint
ms.assetid: 97219bdf-a39a-4e69-81ac-4ca2afe77ce5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 16b05533c566cb90529766d81fb7197dbc284664
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793996"
---
# <a name="idebugapplicationhandlebreakpoint"></a>IDebugApplication::HandleBreakPoint
Powoduje, że bieżący wątek zablokować, a następnie wysyła powiadomienie z informacją o punkt przerwania do debugera w IDE.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT HandleBreakPoint(  
   BREAKREASON         br,  
   BREAKRESUMEACTION*  pbra  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `br`  
 [in] Przyczyna przerwy.  
  
 `pbra`  
 [out] Akcja do wykonania po debuger wznowieniu działania aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Aparat języka wywołuje tę metodę w kontekście wątku, który trafienia punktu przerwania. Ta metoda blokuje bieżącego wątku i wysyła powiadomienia punktu przerwania do debugera w IDE. Gdy debuger wznawia aplikacji, `pbra` parametr określa, jaką akcję należy podjąć.  
  
> [!NOTE]
>  Aparat języka może zostać wywołana przez wątek do wykonywania zadań, takich jak wyliczyć stosu ramki lub obliczać wyrażeń podczas punktu przerwania.  
  
 Ta metoda powoduje `IApplicationDebugger::onHandleBreakPoint` do wywołania.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md)   
 [IApplicationDebugger::onHandleBreakPoint](../../winscript/reference/iapplicationdebugger-onhandlebreakpoint.md)   
 [Wyliczenie BREAKREASON](../../winscript/reference/breakreason-enumeration.md)   
 [Wyliczenie BREAKRESUMEACTION](../../winscript/reference/breakresumeaction-enumeration.md)