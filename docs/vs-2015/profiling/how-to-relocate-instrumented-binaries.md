---
title: 'Porady: przemieszczanie instrumentowanych plików binarny | Dokumentacja firmy Microsoft'
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
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3114ee88feefdbb409ed1a1e1ad025a18123c002
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42681835"
---
# <a name="how-to-relocate-instrumented-binaries"></a>Porady: przemieszczanie instrumentowanych plików binarny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [jak: przemieszczenie Instrumentowane pliki binarne](https://docs.microsoft.com/visualstudio/profiling/how-to-relocate-instrumented-binaries).  
  
Podczas Instrumentacji sondy są wstawiane do plików binarnych do pomiaru wydajności aplikacji. Wybierając Zmień lokalizację instrumentowanych danych binarnych kopię oryginalny plik binarny jest Instrumentacji i umieścić w określonej lokalizacji. Ta opcja jest przydatna, jeśli nie chcesz, aby program profilujący do zmiany nazwy oryginalny plik binarny. Jeśli plik binarny nie został przeniesiony, jest zastępowany oryginalną wersję pliku binarnego.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Aby zmienić lokalizację instrumentowanych danych binarnych  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij **właściwości**.  
  
2.  W **stron właściwości**, kliknij przycisk **binarne** właściwości.  
  
3.  Wybierz **przemieszczanie instrumentowanych plików binarny** pole wyboru.  
  
4.  Określ lokalizację dla instrumentowanego pliku binarnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)



