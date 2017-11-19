---
title: "Kody błędów skryptów aktywnych stałe, wyliczenia i | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: aab24471-5817-45c0-be07-ffe4648923ed
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bb4165a5471c8e79827f0f7605cef575e82bab75
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="active-script-constants-enumerations-and-error-codes"></a>Kody błędów, stałe i wyliczenia aktywnego skryptu
W tej sekcji opisano, wyliczenia i kodów błędów występujących podczas aparaty skryptów systemu Windows.  
  
## <a name="constants"></a>Stałe  
  
|Stała|Opis|  
|--------------|-----------------|  
|[Stałe SCRIPTTHREADID](../../winscript/reference/scriptthreadid-constants.md)|Określa typ wątku.|  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|[Właściwość SCRIPTPROP_HOSTKEEPALIVE](../../winscript/reference/scriptprop-hostkeepalive-property.md)|Służy do określenia, czy aparat skryptów powinny być przechowywane funkcjonalnej, jeśli istnieją oczekujące odwołania.|  
  
## <a name="enumerations"></a>Wyliczenia  
  
|Wyliczenie|Opis|  
|-----------------|-----------------|  
|[Wyliczenie SCRIPTGCTYPE](../../winscript/reference/scriptgctype-enumeration.md)|Typ operacji wyrzucania elementów bezużytecznych do wykonania.|  
|[Wyliczenie SCRIPTLANGUAGEVERSION](../../winscript/reference/scriptlanguageversion-enumeration.md)|Określa możliwości skryptów wersji.|  
|[Wyliczenie SCRIPTSTATE](../../winscript/reference/scriptstate-enumeration.md)|Określa stan aparatu skryptów.|  
|||  
|[Wyliczenie SCRIPTTHREADSTATE](../../winscript/reference/scriptthreadstate-enumeration.md)|Określa stan wątku aparatu skryptów.|  
|[Wyliczenie SCRIPTTRACEINFO](../../winscript/reference/scripttraceinfo-enumeration.md)|Reprezentuje zdarzenia skryptów, które są śledzone. Używane w [metoda IActiveScriptSiteTraceInfo::SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).|  
|[Wyliczenie SCRIPTUICHANDLING](../../winscript/reference/scriptuichandling-enumeration.md)|Przedstawia sposób obsługi formantu interfejsu użytkownika.|  
|[Wyliczenie SCRIPTUICITEM](../../winscript/reference/scriptuicitem-enumeration.md)|Reprezentuje typ elementu interfejsu użytkownika. Używane w [metoda IActiveScriptSiteUIControl::GetUIBehavior](../../winscript/reference/iactivescriptsiteuicontrol-getuibehavior-method.md).|  
  
## <a name="error-codes"></a>Kody błędów  
  
|Kod błędu|Opis|  
|----------------|-----------------|  
|[Kod błędu Script_e_propagate](../../winscript/reference/script-e-propagate-error-code.md)|Błąd skryptu jest przekazywana dalej do elementu wywołującego, która może być w innym wątku.|  
|[Kod błędu Script_e_recorded](../../winscript/reference/script-e-recorded-error-code.md)|Błąd został przekazany między aparat skryptu i hostem.|  
|[Kod błędu Script_e_reported](../../winscript/reference/script-e-reported-error-code.md)|Aparat skryptów zgłosiła nieobsługiwany wyjątek dla hosta.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)