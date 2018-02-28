---
title: IActiveScriptSite | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSite interface
ms.assetid: 4d604a11-5365-46cf-ab71-39b3dbbe9f22
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23dba403a7889fe46817a21ed8e4be65b1c05b4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptsite"></a>IActiveScriptSite
Zaimplementowane przez hosta w celu utworzenia witryny dla aparatów skryptów systemu Windows. Zwykle ta lokacja będzie skojarzona z kontenerem wszystkie obiekty, które są widoczne dla skryptu (na przykład formantów ActiveX). Zazwyczaj ten kontener odpowiada dokumentu lub wyświetlanej stronie. Microsoft Internet Explorer, na przykład utworzyć kontener dla każdej strony HTML będzie wyświetlany. Każdy ActiveX sterowania (lub innego obiektu automatyzacji) na stronie, a aparat skryptów, będzie wyliczalny należących do tego kontenera.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|||  
|-|-|  
|Metoda|Opis|  
|[IActiveScriptSite::GetLCID](../../winscript/reference/iactivescriptsite-getlcid.md)|Pobiera identyfikator ustawień regionalnych, używanego przez hosta do wyświetlania elementów interfejsu użytkownika.|  
|[IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md)|Uzyskiwania informacji na temat elementu, który został dodany do silnika poprzez wywołanie [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) metody.|  
|[IActiveScriptSite::GetDocVersionString](../../winscript/reference/iactivescriptsite-getdocversionstring.md)|Pobiera ciąg zdefiniowany przez hosta, który unikatowo identyfikuje bieżącej wersji dokumentu z punktu widzenia hosta.|  
|[IActiveScriptSite::OnScriptTerminate](../../winscript/reference/iactivescriptsite-onscriptterminate.md)|Wywołuje się po zakończeniu wykonywania skryptu.|  
|[IActiveScriptSite::OnStateChange](../../winscript/reference/iactivescriptsite-onstatechange.md)|Informuje hosta, że aparat skryptów zmieniła się stanów.|  
|[IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md)|Informuje hosta, że wystąpił błąd wykonywania w trakcie aparat skryptu.|  
|[IActiveScriptSite::OnEnterScript](../../winscript/reference/iactivescriptsite-onenterscript.md)|Informuje hosta, że aparat skryptów rozpoczął wykonywanie kodu skryptu.|  
|[IActiveScriptSite::OnLeaveScript](../../winscript/reference/iactivescriptsite-onleavescript.md)|Informuje hosta, że aparat skryptów zwrócił wykonywanie kodu skryptu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)