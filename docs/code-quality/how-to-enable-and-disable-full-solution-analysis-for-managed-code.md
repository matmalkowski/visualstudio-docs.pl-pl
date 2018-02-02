---
title: "Porady: Włączanie i wyłączanie Pełna analiza rozwiązania dla zarządzanego kodu | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 64b541093aaf1a710976c0f53a3214b5d2a47e0d
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Porady: Włączanie i wyłączanie Pełna analiza rozwiązania dla zarządzanego kodu

*Pełna analiza rozwiązania* jest funkcja programu Visual Studio, która umożliwia podgląd problemów dotyczących analizy kodu tylko w otwartych plików Visual C# lub Visual Basic w rozwiązaniu lub także w kodzie pliki, które zostały zamknięte. Domyślnie Pełna analiza rozwiązania jest włączona dla programu Visual Basic i wyłączone Visual C#.

Gdy są widoczne wszystkie problemy we wszystkich plikach jest przydatne, może być rozpraszać. Można również powolne Visual Studio w dół rozwiązania jest bardzo długa lub ma wiele plików. Aby ograniczyć liczbę problemów pokazano i zwiększyć wydajność programu Visual Studio, możesz wyłączyć Pełna analiza rozwiązania. W razie potrzeby można łatwo ponownie włączyć tę funkcję.

## <a name="to-toggle-full-solution-analysis"></a>Aby włączyć pełną analizę rozwiązania

1. Aby otworzyć **opcje** okno dialogowe, na pasku menu programu Visual Studio wybierz **narzędzia** > **opcje**.

1. W **opcje** oknie dialogowym wybierz **Edytor tekstu** > **C#** lub **podstawowe**  >   **Zaawansowane**.

1. Wybierz **Włącz pełną analizę rozwiązania** pole wyboru, aby włączyć pełną analizę rozwiązania, lub wyczyść pole, aby ją wyłączyć. Wybierz **OK** przycisku, gdy wszystko będzie gotowe.

    ![Zaznacz pole wyboru analizy pełnego rozwiązania. ] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")

## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Wyniki Włączanie i wyłączanie Pełna analiza rozwiązania

Na poniższym zrzucie ekranu widać wyniki po włączeniu Pełna analiza rozwiązania. Wszystkie błędy i problemy dotyczące analizy kodu w *wszystkich* plików w rozwiązaniu ma, niezależnie od tego, czy pliki są otwarte, czy nie.

![Pełna analiza rozwiązania włączone. ] (../code-quality/media/fsa_enabled.png "FSA_Enabled")

Poniższy zrzut ekranu przedstawia wyniki z tym samym rozwiązaniu po wyłączeniu Pełna analiza rozwiązania. Tylko błędów i problemów dotyczących analizy kodu w Otwórz rozwiązanie, które pliki są wyświetlane na liście błędów.

![Pełna analiza rozwiązania wyłączone. ] (../code-quality/media/fsa_disabled.png "FSA_Disabled")

## <a name="automatically-disabling-full-solution-analysis"></a>Automatyczne wyłączenie Pełna analiza rozwiązania

Jeśli program Visual Studio wykryje, że 200MB lub mniej pamięci systemowej jest dostępny do niego, on automatycznie wyłącza Pełna analiza rozwiązania (a także kilka innych funkcji) Jeśli jest włączona. W takim przypadku zostanie wyświetlony alert informujący o tym. Przycisk pozwala ponownie włączyć pełną analizę rozwiązania, w razie potrzeby.

![Tekst alertu wstrzymywania Pełna analiza rozwiązania](../code-quality/media/fsa_alert.png "FSA_Alert")