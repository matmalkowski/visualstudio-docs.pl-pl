---
title: Wyliczenie ERRORRESUMEACTION | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- ERRORRESUMEACTION
apilocation:
- scrobj.dll
helpviewer_keywords:
- ERRORRESUMEACTION enumeration
ms.assetid: a68293c8-056b-439f-83e7-69e4a38f4976
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 914c1d7aa4d2935ea94322ebd257f4135d79e9c0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24791692"
---
# <a name="errorresumeaction-enumeration"></a>Wyliczenie ERRORRESUMEACTION
Opisuje sposób kontynuowania pracy po błędzie czasu wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum tagERRORRESUMEACTION {  
   ERRORRESUMEACTION_ReexecuteErrorStatement,  
   ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller,  
   ERRORRESUMEACTION_SkipErrorStatement,  
} ERRORRESUMEACTION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|ERRORRESUMEACTION_ReexecuteErrorStatement|Wykonuje ponownie instrukcji, które spowodowało błąd.|  
|ERRORRESUMEACTION_AbortCallAndReturnErrorToCaller|Umożliwia aparat języka obsługi błędu.|  
|ERRORRESUMEACTION_SkipErrorStatement|Wznawia wykonywanie w kodzie następującej po instrukcji, które spowodowało błąd.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)