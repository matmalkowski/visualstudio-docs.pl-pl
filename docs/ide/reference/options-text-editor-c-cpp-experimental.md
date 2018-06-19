---
title: Opcje, Edytor tekstu, C/C++, eksperymentalne
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: 36826a998c579526487b440ebe9d3ddab228daab
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945974"
---
# <a name="options-text-editor-cc-experimental"></a>Opcje, Edytor tekstu, C/C++, eksperymentalne

Zmieniając opcje te można zmienić zachowanie związane z IntelliSense i przeglądania bazy danych w przypadku programowania C lub C++. Te funkcje są naprawdę eksperymentalne i mogą zostać zmodyfikowane lub usunięte z programu Visual Studio w przyszłej wersji. W tym temacie opisano opcje dostępne w Visual Studio 2017 r. Dla programu Visual Studio 2015, zobacz [opcje, Edytor tekstu, C/C++, eksperymentalne](https://msdn.microsoft.com/library/mt591979.aspx)

Aby uzyskać dostęp do tej strony właściwości, naciśnij klawisz **Control + Q** aktywować `Quick Launch` , a następnie wpisz "eksperymentalne". Szybkie uruchamianie znajdzie strony po pierwsze litery. Można także uzyskać do niego, wybierając **narzędzia | Opcje** i rozszerzanie **Edytor tekstu**, następnie **C/C++**, a następnie wybierając **eksperymentalne**.

Te funkcje są dostępne w instalacji programu Visual Studio 2017 r.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Zobacz [personalizowanie środowiska IDE programu Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Włącz predykcyjnej IntelliSense

IntelliSense predykcyjnej ogranicza liczbę wyników wyświetlanych na liście rozwijanej IntelliSense, aby wyświetlić tylko wyniki, które mają zastosowanie w kontekście. Na przykład jeśli wpiszesz <code>int x =</code> i Wywołaj element dropdown IntelliSense, wyświetlona zostanie tylko liczby całkowite i funkcje, które zwracają liczb całkowitych. Domyślnie predykcyjnej IntelliSense jest wyłączona.

## <a name="enable-faster-project-load"></a>Włącz szybsze ładowania projektu

**Visual Studio 2017 wersji 15.3 i nowszych**: Ta funkcja jest nazywana **Włącz buforowanie projektu** i została przeniesiona do [ustawienia projektu VC ++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) strony właściwości.
Ta opcja umożliwia Visual Studio do pamięci podręcznej danych projektu tak, aby po przy następnym otwarciu projektu go załadować tych buforowanych danych, zamiast ponownego przetwarzania danych z plików projektu. Przy użyciu danych z pamięci podręcznej można skrócić czas ładowania projektu znacznie.

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Dodatkowe funkcje w witrynie Marketplace programu Visual Studio

Możesz przeglądać funkcje edycji dodatkowy tekst w [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Na przykład [C++ szybkie rozwiązania](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017), który obsługuje następujące:

- **Dodaj brakujące #include** -sugeruje odpowiednich #include na nieznany symboli w kodzie

- **Dodawanie przy użyciu przestrzeni nazw/pełnej kwalifikacji symbol** — podobnie jak poprzedniego elementu, ale w przypadku przestrzeni nazw

- **Dodaj brakujące średnikami**

- **Pomoc online** -wyszukiwania pomocy online komunikaty o błędach

- i więcej...

## <a name="see-also"></a>Zobacz także

- [Ustawianie opcji edytora specyficznych dla języka](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoryzacja w języku C++ (VC Blog)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
