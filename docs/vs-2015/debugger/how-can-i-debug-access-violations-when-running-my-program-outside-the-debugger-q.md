---
title: W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem? | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1525061210c6ef7cdda32c6204648c3944f4b889
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42632364"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak mogę debugować dostępu naruszeń podczas uruchamiania Moje poza debugera programu?](https://docs.microsoft.com/visualstudio/debugger/how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger-q).  
  
Opis problemu  
 Program działa poprawnie w środowisku Visual Studio, ale gdy uruchamiam go autonomicznego w systemie operacyjnym Windows, generuje naruszenie zasad dostępu. W jaki sposób można debugować ten problem?  
  
## <a name="solution"></a>Rozwiązanie  
 Ustaw [Just-in-time debugging](../debugger/just-in-time-debugging-in-visual-studio.md) opcji, a następnie uruchom program autonomiczny, dopóki nie nastąpi naruszenie zasad dostępu. Następnie w **naruszenie zasad dostępu** okno dialogowe, możesz kliknąć pozycję **anulować** można uruchomić debugera.  
  
 Zobacz też artykuł bazy wiedzy Knowledge Base Q133174, "Jak do lokalizacji, w którym występuje ogólny błąd ochrony (GP)". Można znaleźć artykuły bazy wiedzy na dysku CD z biblioteki MSDN lub przeszukując [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)



