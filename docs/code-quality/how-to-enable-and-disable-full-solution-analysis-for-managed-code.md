---
title: 'Porady: Włączanie i wyłączanie Pełna analiza rozwiązania dla zarządzanego kodu | Dokumentacja firmy Microsoft'
ms.date: 03/23/2018
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 4c5985792138d334de103523478841917555fc56
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Porady: Włączanie i wyłączanie Pełna analiza rozwiązania dla zarządzanego kodu

*Pełna analiza rozwiązania* jest funkcja programu Visual Studio, która umożliwia podgląd problemów dotyczących analizy kodu tylko w otwartych plików Visual C# lub Visual Basic w rozwiązaniu lub także w kodzie pliki, które zostały zamknięte. Domyślnie jest Pełna analiza rozwiązania *włączone* w języku Visual Basic i *wyłączone* Visual C#.

Można jej użyć wyświetlić wszystkie problemy we wszystkich plikach, ale może też być rozpraszać. Go spowalnia Visual Studio Jeśli rozwiązanie jest bardzo długa lub zawiera wiele plików. Aby ograniczyć liczbę problemów pokazano i zwiększyć wydajność programu Visual Studio, możesz wyłączyć Pełna analiza rozwiązania. W razie potrzeby można łatwo ponownie włączyć tę funkcję.

## <a name="to-toggle-full-solution-analysis"></a>Aby włączyć pełną analizę rozwiązania

1. Aby otworzyć **opcje** okno dialogowe, na pasku menu programu Visual Studio wybierz **narzędzia** > **opcje**.

1. W **opcje** oknie dialogowym wybierz **Edytor tekstu** > **C#** lub **podstawowe**  >   **Zaawansowane**.

1. Wybierz **Włącz pełną analizę rozwiązania** pole wyboru, aby włączyć pełną analizę rozwiązania, lub wyczyść pole, aby ją wyłączyć. Wybierz **OK** po zakończeniu.

    ![Zaznacz pole wyboru analizy pełnego rozwiązania.](../code-quality/media/options-enable-full-solution-analysis.png)

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Wyniki Włączanie i wyłączanie Pełna analiza rozwiązania

Na poniższym zrzucie ekranu widać wyniki po włączeniu Pełna analiza rozwiązania. Wszystkie błędy i problemy dotyczące analizy kodu w *wszystkich* plików w rozwiązaniu ma, niezależnie od tego, czy pliki są otwarte, czy nie.

![Pełna analiza rozwiązania włączone.](../code-quality/media/fsa_enabled.png)

Poniższy zrzut ekranu przedstawia wyniki z tym samym rozwiązaniu po wyłączeniu Pełna analiza rozwiązania. Tylko błędów i problemów dotyczących analizy kodu w plikach Otwórz rozwiązanie **listy błędów**.

![Pełna analiza rozwiązania wyłączone.](../code-quality/media/fsa_disabled.png)

## <a name="automatically-disable-full-solution-analysis"></a>Automatycznie wyłączyć Pełna analiza rozwiązania

Jeśli program Visual Studio wykryje, że 200 MB lub mniej pamięci systemowej jest dostępne, on automatycznie wyłącza Pełna analiza rozwiązania (i inne funkcje) Jeśli jest włączona. W takim przypadku zostanie wyświetlony alert informujący o tym, że program Visual Studio ma wyłączone niektóre funkcje. Przycisk pozwala włączyć pełną analizę rozwiązania, jeśli chcesz.

![Tekst alertu wstrzymywania Pełna analiza rozwiązania](../code-quality/media/fsa_alert.png)