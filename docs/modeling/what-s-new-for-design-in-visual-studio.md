---
title: Co nowego w dziedzinie projektowania w programie Visual Studio
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio ALM], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio ALM], What's New
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c25d89ae3ab3d25e415b4407a46fc903b1c05266
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="whats-new-for-design-in-visual-studio"></a>Co nowego w dziedzinie projektowania w programie Visual Studio

## <a name="live-dependency-validation"></a>Sprawdzanie poprawności zależności na żywo

Usuwanie zależności niechciane jest ważnym elementem zarządzania z dług technicznych. Na żywo walidacji zależności jest teraz włączone, zapewniając dokładne informacje o problemach i pełni korzystających z nowych funkcji w edytorze i na liście błędów.

![Sprawdzanie poprawności zależności na żywo w akcji](media/dep-validation-whatsnew-01.png)

Środowisko tworzenia zmienił się dokonanie walidacji zależności mogą szybciej odnajdywać i jest bardziej dostępny, zmiana terminologii z "Diagram warstwowy" do "Zależności diagramu".

**Architektura** menu zawiera teraz polecenia można bezpośrednio utworzyć diagram zależności:

![Element zależności na żywo menu architektury](media/dep-validation-whatsnew-02.png)

... i zostały zmienione nazwy właściwości warstwy w diagramie zależności i ich opisy, aby były bardziej zrozumiałe:

![Nazwy właściwości zależności na żywo zaktualizowane](media/dep-validation-whatsnew-03.png)

Pojawi się wpływ zmiany bezpośrednio w wynikach analizy dla bieżącego kodu w rozwiązaniu zawsze zapisywania diagramu. Nie masz już oczekiwania na wykonanie polecenia "Zweryfikować zależności".

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/07/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Usunięto projektantów UML

Projektanci UML zostały usunięte z tej wersji programu Visual Studio Enterprise.

* Diagramy UML są teraz widoczne jako pliki XML
* Eksplorator modelu UML już nie istnieje.
* Modelowanie odwołań nie są już używane do walidacji zależności projektu
* Węzeł "Odwołania do warstwy" w Eksploratorze rozwiązań nie będzie już wyświetlany
* Akcja kompilacji "Weryfikuj" na diagramie zależności (warstwy) nie jest już używany — zadania kompilacji został usunięty.
* Struktury projektu jest zachowywana na potrzeby dwustronną komunikację między wersjami
* Można nadal otworzyć, tworzenie, edytowanie i Zapisz diagram zależności (warstwy) jako XML
* Połączone z diagramu zależności (warstwy) elementów roboczych TFS nie są dostępne na powierzchnię projektu
* Wstecz łączenie z DSL lub warstwy nie jest już obsługiwana
* Rozszerzalność UML w zestawie SDK modelowania nie jest już obsługiwana

Jednak obsługa wizualizacja architektury .NET i C++ kod jest dostępna za pośrednictwem [code map](map-dependencies-across-your-solutions.md)i wprowadzono znaczne ulepszenia do walidacji zależności opisane powyżej.

Jeśli jesteś użytkownikiem znaczących projektantów UML można nadal używać programu Visual Studio 2015 i jego wcześniejsze wersje podczas podejmowanie decyzji o alternatywnych narzędzia do potrzeb UML.

Aby uzyskać więcej informacji, zobacz [ten wpis w blogu](https://blogs.msdn.microsoft.com/visualstudioalm/2016/10/14/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-version-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Obsługa wersji architektura i modelowanie narzędzia

Visual Studio 2015 jest dostępna w kilku różnych wersjach. Nie wszystkie te zapewniają obsługę architektura i modelowanie narzędzi. W poniższej tabeli przedstawiono Dostępność poszczególnych narzędzi.

|**Funkcja**|**Enterprise**|**Professional**|**Community**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mapy kodu**|Tak|Mapuje tylko filtrowania kod obsługuje odczytywanie mapy kodu, dodawanie nowych węzłów ogólnego i tworzenie nowego wykresu skierowane do zaznaczenia.|-|-|
|**Diagramy zależności**|Tak|Obsługuje tylko odczytywanie diagramy zależności.|Obsługuje tylko odczytywanie diagramy zależności.|-|
|**Przekierowanie wykresy** (DGML diagramy)|Tak|Tak|Tak|-|
|**Klonu kodu**|Tak|-|-|-|