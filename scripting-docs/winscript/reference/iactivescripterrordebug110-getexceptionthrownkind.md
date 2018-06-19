---
title: IActiveScriptErrorDebug110::GetExceptionThrownKind | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptErrorDebug110::QueryIsFirstChance
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8306b1d4ff68fe9eec00d47d8c702278e89fc37b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
ms.locfileid: "24793372"
---
# <a name="iactivescripterrordebug110getexceptionthrownkind"></a>IActiveScriptErrorDebug110::GetExceptionThrownKind
Zwraca wartość wskazującą rodzaj zgłaszanego wyjątku.  
  
> [!IMPORTANT]
>  [Interfejs IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md) jest implementowany przez PDM wersji 11.0 lub nowszej. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pExceptionKind`  
 [out] Rodzaj wyjątek zgłaszany (na przykład pierwszej szansy lub nieobsługiwany), reprezentowany przez [wyliczenie SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md) wartości wyliczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs IActiveScriptErrorDebug110](../../winscript/reference/iactivescripterrordebug110-interface.md)