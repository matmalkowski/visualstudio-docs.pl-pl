---
title: "Porady: przemieszczanie instrumentowanych plików binarny | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 72c15bfc5449a1dab516be217da4a76276312fd3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-relocate-instrumented-binaries"></a>Porady: przemieszczanie instrumentowanych plików binarny
Podczas Instrumentacji sond są wstawiane do pliku binarnego do pomiaru wydajności aplikacji. Wybierając może przenosić instrumentowanego pliku binarnego, kopia oryginalnego pliku binarnego jest instrumentowany i umieszcza w określonej lokalizacji. Ta opcja jest przydatna, jeśli nie chcesz profilera, aby zmienić nazwę z oryginalnego pliku binarnego. Jeśli plik binarny nie został przeniesiony, jest zastępowany oryginalną wersją pliku binarnego.  
  
 **Wymagania**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>Aby przenieść instrumentowanego pliku binarnego  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij przycisk **właściwości**.  
  
2.  W **strony właściwości**, kliknij przycisk **binarne** właściwości.  
  
3.  Wybierz **przemieszczanie instrumentowanych plików binarny** pole wyboru.  
  
4.  Określ lokalizację dla instrumentowanego pliku binarnego.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)