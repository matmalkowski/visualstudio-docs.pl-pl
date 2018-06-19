---
title: IActiveScript | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScript interface
ms.assetid: d8acee11-7f0d-4999-b97a-66774af16f71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68d91a7ad91364d0c2133150d76cdb221929b16b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793297"
---
# <a name="iactivescript"></a>IActiveScript
Udostępnia metody, które są niezbędne do zainicjowania aparatu skryptów. Aparat skryptów musi implementować `IActiveScript` interfejsu.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md)|Informuje o aparat skryptów z [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) lokacja dostarczonych przez hosta.|  
|[IActiveScript::GetScriptSite](../../winscript/reference/iactivescript-getscriptsite.md)|Pobiera obiekt lokacji skojarzonego z aparatem skryptów systemu Windows.|  
|[IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md)|Umieszcza aparat skryptów w określonym stanie.|  
|[IActiveScript::GetScriptState](../../winscript/reference/iactivescript-getscriptstate.md)|Pobiera bieżący stan aparatu skryptów.|  
|[IActiveScript::Close](../../winscript/reference/iactivescript-close.md)|Powoduje, że aparat skryptów abandon dowolnego skryptu aktualnie załadowanych utratę stanu i zwolnić wszystkie wskaźniki interfejsu, wymagana jest wartość inne obiekty, w związku z tym wprowadzanie stanie zamkniętym.|  
|[IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md)|Dodaje nazwę elementu głównego poziomu do przestrzeni nazw aparatu skryptów.|  
|[IActiveScript::AddTypeLib](../../winscript/reference/iactivescript-addtypelib.md)|Dodaje bibliotekę typów do przestrzeni nazw dla skryptu.|  
|[IActiveScript::GetScriptDispatch](../../winscript/reference/iactivescript-getscriptdispatch.md)|Pobiera `IDispatch` interfejs dla uruchamianie skryptu.|  
|[IActiveScript::GetCurrentScriptThreadID](../../winscript/reference/iactivescript-getcurrentscriptthreadid.md)|Pobiera identyfikator skryptów aparatu zdefiniowanych dla wątku aktualnie wykonywane.|  
|[IActiveScript::GetScriptThreadID](../../winscript/reference/iactivescript-getscriptthreadid.md)|Pobiera identyfikator skryptów aparatu zdefiniowanych dla wątku skojarzone z danym wątku Microsoft Win32.|  
|[IActiveScript::GetScriptThreadState](../../winscript/reference/iactivescript-getscriptthreadstate.md)|Pobiera bieżący stan wątku skryptu.|  
|[IActiveScript::InterruptScriptThread](../../winscript/reference/iactivescript-interruptscriptthread.md)|Przerwanie wykonywania uruchomiony wątek skryptu.|  
|[IActiveScript::Clone](../../winscript/reference/iactivescript-clone.md)|Klonów bieżącego aparatu skryptów (minus wszelkie bieżący stan wykonania), zwracając załadować aparatów skryptów, który ma żadna lokacja w bieżącym wątku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołania skryptów systemu Windows](../../winscript/reference/windows-script-interfaces-reference.md)