---
title: IActiveScriptError | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IActiveScriptError interface
ms.assetid: c8e0288d-38ff-4145-a7e3-f8cdfb72eefe
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a403bf412a0c93a5c435e1a3184202ed68d406ea
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescripterror"></a>IActiveScriptError
Obiekt zawierający implementację tego interfejsu jest przekazywany do [IActiveScriptSite::OnScriptError](../../winscript/reference/iactivescriptsite-onscripterror.md) metody zawsze, gdy aparat skryptów napotka nieobsługiwany błąd. Host następnie wywołuje metody dla tego obiektu, aby uzyskać informacje o błędzie, który wystąpił.  
  
## <a name="methods-in-vtable-order"></a>Metody w kolejności Vtable  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptError::GetExceptionInfo](../../winscript/reference/iactivescripterror-getexceptioninfo.md)|Pobiera informacje o błędzie.|  
|[IActiveScriptError::GetSourcePosition](../../winscript/reference/iactivescripterror-getsourceposition.md)|Pobiera lokalizacji w kodzie źródłowym, w którym wystąpił błąd.|  
|[IActiveScriptError::GetSourceLineText](../../winscript/reference/iactivescripterror-getsourcelinetext.md)|Pobiera wiersz w pliku źródłowym, w którym wystąpił błąd.|  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy aktywnego skryptu](../../winscript/reference/active-script-interfaces.md)