---
title: "Porady: Włączanie i wyłączanie Pełna analiza rozwiązania dla zarządzanego kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 94cda949a713a773e5586e5b1ef284c6ba54839c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Porady: Włączanie i wyłączanie Pełna analiza rozwiązania dla zarządzanego kodu
> [!NOTE]
>  Ten temat dotyczy tylko programu Visual Studio 2015 Update 3 RC i nowszych.  
  
 *Pełna analiza rozwiązania* jest funkcja programu Visual Studio, który umożliwia wybranie, czy wyświetlać problemów dotyczących analizy kodu tylko w otwartych plików Visual C# lub Visual Basic w rozwiązaniu lub w otwartych i zamkniętych plikach języka Visual C# lub Visual Basic w rozwiązaniu.  
  
 Gdy są widoczne wszystkie problemy we wszystkich plikach jest przydatne, może być rozpraszać uwagę czytelników i nawet spowolnić Visual Studio rozwiązania jest bardzo długa lub ma wiele plików.  Aby ograniczyć liczbę problemów pokazano i zwiększyć wydajność programu Visual Studio, możesz wyłączyć Pełna analiza rozwiązania. Jeśli chcesz, można łatwo ponownie włączyć tę funkcję.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Aby włączyć pełną analizę rozwiązania  
  
1.  W menu głównym w programie Visual Studio wybierz **narzędzia** &#124; **Opcje** Aby wyświetlić **opcje** okno dialogowe.  
  
2.  W **opcje** oknie dialogowym wybierz **Edytor tekstu** &#124; **C#** lub **podstawowe** &#124; **Zaawansowane**.  
  
3.  Wybierz **Włącz pełną analizę rozwiązania** pole wyboru, aby włączyć pełną analizę rozwiązania, lub wyczyść pole, aby ją wyłączyć. Wybierz **OK** przycisku, gdy wszystko będzie gotowe.  
  
     ![Zaznacz pole wyboru analizy pełnego rozwiązania. ] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Wyniki Włączanie i wyłączanie Pełna analiza rozwiązania  
 Na poniższym zrzucie ekranu widać wyniki po włączeniu Pełna analiza rozwiązania. Wszystkie błędy i problemy dotyczące analizy kodu w *wszystkich* plików w rozwiązaniu ma, niezależnie od tego, czy pliki są otwarte, czy nie.  
  
 ![Pełna analiza rozwiązania włączone. ] (../code-quality/media/fsa_enabled.png "FSA_Enabled")  
  
 Poniższy zrzut ekranu przedstawia wyniki z tym samym rozwiązaniu po wyłączeniu Pełna analiza rozwiązania. Tylko błędów i problemów dotyczących analizy kodu w Otwórz rozwiązanie, które pliki są wyświetlane na liście błędów.  
  
 ![Pełna analiza rozwiązania wyłączone. ] (../code-quality/media/fsa_disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Automatyczne wyłączenie Pełna analiza rozwiązania  
 Jeśli program Visual Studio wykryje, że 200MB lub mniej pamięci systemowej jest dostępny do niego, on automatycznie wyłącza Pełna analiza rozwiązania (a także kilka innych funkcji) Jeśli jest włączona. W takim przypadku zostanie wyświetlony alert informujący o tym. Przycisk pozwala ponownie włączyć pełną analizę rozwiązania, jeśli chcesz to zrobić.  
  
 ![Tekst alertu wstrzymywania Pełna analiza rozwiązania](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Dodatkowe szczegóły  
 Domyślnie Pełna analiza rozwiązania jest włączona dla programu Visual Basic i wyłączone Visual C#.  
  
 Visual Studio Update 3 RC zawiera aparat diagnostycznych v2 analizatora rozszerzonego kodu, który znacznie zmniejsza użycie pamięci i zmniejsza czas procesora CPU w stan bezczynności, nawet gdy włączone jest Pełna analiza rozwiązania.