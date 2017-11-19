---
title: "W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem? | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d1b8a6e019725f95788b4988fbe1ddef18cb27cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem?
## <a name="problem-description"></a>Opis problemu  
 Program działa poprawnie w środowisku Visual Studio, ale po uruchomieniu go autonomicznym z systemem operacyjnym Windows, generuje naruszenia zasad dostępu. Jak można debugować ten problem?  
  
## <a name="solution"></a>Rozwiązanie  
 Ustaw [Just in time debugowania](../debugger/just-in-time-debugging-in-visual-studio.md) opcji i uruchomić program autonomicznej, do momentu naruszenia zasad dostępu. Następnie w **naruszenie zasad dostępu** okno dialogowe, możesz kliknąć **anulować** można uruchomić debugera.  
  
 Zobacz też w artykule bazy wiedzy Q133174, "Jak zlokalizuj, gdzie występuje ogólny błąd ochrony (GP)". Można znaleźć artykuły bazy wiedzy na dysku CD biblioteki MSDN lub wyszukując [http://support.microsoft.com/](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)