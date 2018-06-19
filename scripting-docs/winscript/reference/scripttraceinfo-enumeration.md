---
title: Wyliczenie SCRIPTTRACEINFO | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: cb8a4767-8c8e-4fa0-a735-038767a8c500
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc1902b290a8024679cef12d503e94de4923defb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24796351"
---
# <a name="scripttraceinfo-enumeration"></a>Wyliczenie SCRIPTTRACEINFO
Reprezentuje zdarzenia skryptów, które są śledzone. Używane w [metoda IActiveScriptSiteTraceInfo::SendScriptTraceInfo](../../winscript/reference/iactivescriptsitetraceinfo-sendscripttraceinfo-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum tagSCRIPTTRACEINFO {      SCRIPTTRACEINFO_SCRIPTSTART = 0,      SCRIPTTRACEINFO_SCRIPTEND   = 1,      SCRIPTTRACEINFO_COMCALLSTART    = 2,      SCRIPTTRACEINFO_COMCALLEND  = 3,      SCRIPTTRACEINFO_CREATEOBJSTART  = 4,      SCRIPTTRACEINFO_CREATEOBJEND    = 5,      SCRIPTTRACEINFO_GETOBJSTART = 6,      SCRIPTTRACEINFO_GETOBJEND   = 7,  } SCRIPTTRACEINFO ;  
```  
  
## <a name="enumeration-values"></a>Wartości wyliczenia  
  
|||  
|-|-|  
|SCRIPTTRACEINFO_SCRIPTSTART|Początek skryptu.|  
|SCRIPTTRACEINFO_SCRIPTEND|Koniec skryptu.|  
|SCRIPTTRACEINFO_COMCALLSTART|Początek wywołania COM.|  
|SCRIPTTRACEINFO_COMCALLEND|Koniec wywołania modelu COM.|  
|SCRIPTTRACEINFO_CREATEOBJSTART|Data rozpoczęcia tworzenia obiektów.|  
|SCRIPTTRACEINFO_CREATEOBJEND|Data zakończenia tworzenia obiektów.|  
|SCRIPTTRACEINFO_GETOBJSTART|Początek wywołania GetObject.|  
|SCRIPTTRACEINFO_GETOBJEND|Koniec wywołania GetObject.|