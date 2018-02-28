---
title: "Hosty skryptów systemu Windows | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Script Host, implementing hosts
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 41fa898c7f0d62cd35cc1cb1c7b35eb2651c8bb6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2017
---
# <a name="windows-script-hosts"></a>Hosty skryptów systemu Windows
Podczas wdrażania hosta skryptów systemu Windows firmy Microsoft, można bezpiecznie przyjąć aparat skryptów tylko wywołuje [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejsu w kontekście wątku podstawowego tak długo, jak host wykonuje następujące czynności:  
  
-   Wybiera podstawowy wątku (zazwyczaj wątku, który zawiera pętlę komunikatów).  
  
-   Tworzy wystąpienie aparatu skryptów w podstawowy wątku.  
  
-   Wywołania skryptów aparatu metody tylko z wątku podstawowej, z wyjątkiem, gdy jest to dozwolone w szczególności, jak w przypadku [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) i [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
-   Wywołanie obiektu dyspozytora aparat skryptów tylko z wątku podstawowej.  
  
-   Zapewnia, że pętli komunikatów działa w podstawowej wątku, jeśli podano uchwytu okna.  
  
-   Zapewnia, że obiekty w obiekcie hosta modelu tylko źródło zdarzeń w podstawowy wątku.  
  
 Te reguły są automatycznie po wszystkie hosty jednowątkowy. Model ograniczeniami opisany powyżej jest celowo utracić wystarczająco umożliwia hosta przerwanie skryptu zablokowane przez wywołanie metody [IActiveScript::InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) z innego wątku (inicjowane przez program obsługi CTRL + BREAK lub podobnych) lub do Zduplikowana skryptu za pomocą nowego wątku [IActiveScript::Clone](../winscript/reference/iactivescript-clone.md).  
  
## <a name="remarks"></a>Uwagi  
 Żadna z tych ograniczeń dotyczą hosta, który wybiera do zaimplementowania bezwątkowe [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) interfejs oraz model obiektu bezwątkowy. Nieznany host można użyć [IActiveScript](../winscript/reference/iactivescript.md) interfejsu z dowolnego wątku bez ograniczeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy skryptów systemu Windows](../winscript/windows-script-interfaces.md)