---
title: "W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 9b78b679878a68505162b6edd3fcd23403c8d07c
ms.sourcegitcommit: 342e5ec5cec4d07864d65379c2add5cec247f3d6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2018
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem?
## <a name="problem-description"></a>Opis problemu  
 Program działa poprawnie w środowisku Visual Studio, ale po uruchomieniu go autonomicznym z systemem operacyjnym Windows, generuje naruszenia zasad dostępu. Jak można debugować ten problem?  
  
## <a name="solution"></a>Rozwiązanie  
 Ustaw [Just in time debugowania](../debugger/just-in-time-debugging-in-visual-studio.md) opcji i uruchomić program autonomicznej, do momentu naruszenia zasad dostępu. Następnie w **naruszenie zasad dostępu** okno dialogowe, możesz kliknąć **anulować** można uruchomić debugera.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)