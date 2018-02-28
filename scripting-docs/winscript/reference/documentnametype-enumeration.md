---
title: Wyliczenie DOCUMENTNAMETYPE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- DOCUMENTNAMETYPE
apilocation:
- scrobj.dll
helpviewer_keywords:
- DOCUMENTNAMETYPE enumeration
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a0bd21dddd209f21ae64ea2775bbaa0da226f077
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="documentnametype-enumeration"></a>Wyliczenie DOCUMENTNAMETYPE
Wskazuje, który typ ma zostać pobrany dla dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,} DOCUMENTNAMETYPE;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|DOCUMENTNAMETYPE_APPNODE|Pobiera nazwę wyświetlaną w drzewie aplikacji.|  
|DOCUMENTNAMETYPE_TITLE|Pobiera nazwę wyświetlaną na pasku tytułu podglądu.|  
|DOCUMENTNAMETYPE_FILE_TAIL|Pobiera nazwę pliku bez ścieżki.|  
|DOCUMENTNAMETYPE_URL|Pobiera adres URL dokumentu.|  
|DOCUMENTNAMETYPE_UNIQUE_TITLE|Pobiera tytuł dołączony wyliczenie do identyfikacji.|  
  
## <a name="see-also"></a>Zobacz też  
 [Stałe debugera aktywnego skryptu, wyliczenia i struktury](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)