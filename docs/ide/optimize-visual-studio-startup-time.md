---
title: Zwiększyć czas uruchamiania programu Visual Studio
ms.date: 11/15/2017
ms.topic: conceptual
helpviewer_keywords:
- startup time [Visual Studio]
- optimizing performance [Visual Studio]
- speed up start time [Visual Studio]
ms.assetid: d1508121-8499-4084-8eb5-fa89fa7b17d3
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.performancecenter
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 451238283e5f256f9c7c302bd81dd45ad2825cf4
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36233811"
---
# <a name="optimize-visual-studio-startup-time"></a>Optymalizuj czas uruchamiania programu Visual Studio

Program Visual Studio jest przeznaczony do uruchamiania tak szybko i wydajnie, jak to możliwe. Jednak niektóre rozszerzenia programu Visual Studio i okien narzędzi może niekorzystnie wpłynąć na czas uruchamiania, gdy są załadowane. Można kontrolować zachowanie powolne rozszerzenia i okien narzędzi w **zarządzanie wydajnością programu Visual Studio** okno dialogowe. Aby uzyskać bardziej ogólne porady dotyczące poprawy wydajności, zobacz [i porady dotyczące wydajności programu Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md).

## <a name="startup-behavior"></a>Zachowanie podczas uruchamiania

Aby uniknąć rozszerzanie czas uruchamiania, Visual Studio 2017 ładuje rozszerzeń przy użyciu _na żądanie_ podejście. To zachowanie oznacza, że rozszerzenia nie otwieraj natychmiast po uruchomieniu programu Visual Studio, ale na zgodnie z potrzebami. Ponieważ narzędzie windows otwarte w poprzedniej sesji programu Visual Studio może spowolnić uruchamianie, Visual Studio otwiera również okna narzędzi w sposób bardziej inteligentne, aby uniknąć wpływu na czas uruchamiania.

Jeśli program Visual Studio wykryje powolne uruchomienia, pojawi się komunikat podręczny wysyłać alerty o oknie rozszerzenia lub narzędzia, które powoduje spowolnienie. Komunikat zawiera link do **zarządzanie wydajnością programu Visual Studio** okno dialogowe. Można również otworzyć to okno dialogowe, wybierając **pomocy** > **zarządzanie wydajnością programu Visual Studio** na pasku menu.

![Zarządzanie Visual Studio wydajności — podręczny odczytywania "Zauważyliśmy, że rozszerzenia... spowalnia Visual Studio"](../ide/media/vside_perfdialog_popup.png)

Okno dialogowe wyświetla okna narzędzia i rozszerzenia, które mają wpływ na wydajność uruchamiania. Możesz zmienić ustawienia okna narzędzia i rozszerzenia do zwiększenia wydajności uruchamiania.

## <a name="a-nameextensions-to-change-extension-settings-to-improve-startup-solution-load-and-typing-performance"></a><a name="extensions" />Aby zmienić ustawienia rozszerzenia zwiększające uruchamiania, ładowania rozwiązania i wpisując wydajności

1. Otwórz **zarządzanie wydajnością programu Visual Studio** okno dialogowe, wybierając **pomocy** > **zarządzanie wydajnością programu Visual Studio** na pasku menu.

    Jeśli rozszerzenie jest zmniejszają uruchamiania programu Visual Studio, rozwiązania ładowania, lub wpisując, rozszerzenie zostanie wyświetlony w **zarządzanie wydajnością programu Visual Studio** okno dialogowe, w obszarze **rozszerzenia**  >   **Uruchamianie** (lub **ładowania rozwiązania** lub **wpisując**).

    ![Zarządzanie wydajności programu Visual Studio — widok rozszerzeń](../ide/media/vside_perfdialog_extensions.png)

2. Wybierz rozszerzenia, aby wyłączyć, a następnie wybierz pozycję **wyłączyć** przycisku.

Można zawsze ponownie włączyć rozszerzenie dla przyszłych sesji przy użyciu **Menedżera rozszerzenia** lub **zarządzanie wydajnością programu Visual Studio** okno dialogowe.

## <a name="a-nametool-windows-to-change-tool-window-settings-to-improve-startup-time"></a><a name="tool-windows" />Aby zmienić ustawienia okna narzędzia, aby zwiększyć czas uruchamiania

1. Otwórz **zarządzanie wydajnością programu Visual Studio** okno dialogowe, wybierając **pomocy** > **zarządzanie wydajnością programu Visual Studio** na pasku menu.

    Jeśli okno narzędzia jest spowolnieniem uruchamiania programu Visual Studio, okna narzędzia jest wyświetlana w **zarządzanie wydajnością programu Visual Studio** okno dialogowe, w obszarze **okna narzędzi** > **uruchamiania**.

2. Wybierz okna narzędzia, aby zmienić zachowanie.

3. Wybierz jedną z trzech opcji:

    - **Użyj domyślnego zachowania:** domyślne zachowanie dla okna narzędzia. Utrzymywanie wybrania tej opcji nie poprawi wydajność uruchamiania.

    - **Nie pokazuj okna przy uruchamianiu:** określonego narzędzia zawsze zamknięcia okna po otwarciu programu Visual Studio, nawet jeśli jego otwarte w poprzedniej sesji. W razie konieczności można otworzyć okna narzędzia odpowiednie menu.

    - **Automatyczne ukrywanie okna przy uruchamianiu:** Jeśli okno narzędzia zostało otwarte w poprzedniej sesji, ta opcja zwija okna narzędzia grupy przy uruchamianiu, aby uniknąć inicjowania okna narzędzia. Ta opcja jest dobrym rozwiązaniem, jeśli często używasz okna narzędzia. Okna narzędzi jest nadal dostępne, ale nie będzie miało negatywny wpływ na czas uruchamiania programu Visual Studio.

    ![Zarządzanie wydajnością programu Visual Studio — wyświetlanie okna narzędzi](../ide/media/vside_perfdialog_toolwindows.png)

> [!NOTE]
> Niektóre starsze wersje programu Visual Studio 2017 ma funkcję **ładowania rozwiązania lekkie**. Ta funkcja nie jest już dostępna w wersji Visual Studio 2017 15,5 cala lub nowszy. W Visual Studio 2017 wersji 15.5 i nowszych dużych rozwiązaniach, które zawierają zarządzanego kodu obciążenia znacznie szybsze niż wcześniej, nawet bez obciążenia lekkie rozwiązanie.

## <a name="see-also"></a>Zobacz także

- [Optymalizacja wydajności programu Visual Studio](../ide/optimize-visual-studio-performance.md)
- [Visual Studio wydajności porady i wskazówki](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blogu — rozwiązania obciążenia szybsze z programu Visual Studio 2017 wersji 15,6](https://blogs.msdn.microsoft.com/visualstudio/2018/04/04/load-solutions-faster-with-visual-studio-2017-version-15-6/)