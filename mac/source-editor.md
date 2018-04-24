---
title: Edytor źródła
description: Za pomocą edytora źródła w programie Visual Studio dla komputerów Mac
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: 8d2874b731bf0ad54b4a596034a23af8815fa502
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="source-editor"></a>Edytor źródła

Edytor wiarygodnego źródła jest konieczne do pisania kodu krótkiej formie i wydajne. Programu Visual Studio for Mac zawiera Edytor zaawansowane źródła, który znajduje się na środku interakcji z IDE. Edytor źródła zawiera funkcje, które mogą oczekiwać, należy wykonać swoją pracę z łatwością: od podstaw takie wyróżnianie składni, fragmentów kodu i składania kodu, do korzystania z integracji kompilatora Roslyn, takie jak IntelliSense funkcjonalnej kodu ukończenia.

Edytor źródła w programie Visual Studio for Mac umożliwia bezproblemowe ze wszystkimi funkcjami w środowisku IDE, takie jak debugowania, refaktoryzacji elementu i integracją kontroli wersji.

W tym artykule przedstawiono niektóre główne funkcje Edytor źródła i opisuje, jak można programu Visual Studio for Mac produktywność jak to możliwe.

## <a name="the-source-editor-experience"></a>Środowisko Edytor źródła

Wyświetlanie i przenoszenie wydajnie w całym kodzie jest integralną częścią przepływu pracy programowania. Dokładnie, jak użytkownik chce wyświetlać i obsługa, że kod jest osobiste decyzji, który różni się między deweloperzy - i często między projektami.

Program Visual Studio dla komputerów Mac oferuje wiele zaawansowanych funkcji, aby wiele platform jako dostępny i użyteczna, jak to możliwe. W poniższych sekcjach opisano niektóre najważniejsze funkcje.


## <a name="code-folding"></a>Składanie kodu

Kod składania ułatwia zarządzanie plików kodu źródłowego dużych przez deweloperów pokazać lub ukryć pełną części kodu, na przykład przy użyciu dyrektyw, schematyczny kod i komentarze i instrukcje #region. Składanie kodu jest domyślnie wyłączona w programie Visual Studio dla komputerów Mac

Aby włączyć składania kodu, przejdź do **programu Visual Studio > Preferencje... > Edytor tekstu > Ogólne > Kod składania**:

![Kod składania opcje](media/source-editor-image1.png)

To menu zawiera również opcję fold #regions i komentarze domyślnie wyświetlania o nazwie wskazówki, zamiast kodu.

Aby pokazać lub ukryć sekcje, należy użyć widget ujawniania obok numer wiersza:

 ![Pokazywanie lub ukrywanie sekcje w kodzie](media/source-editor-image2.png)

Można również przełączać się między pokazywanie i ukrywanie złożeń przy użyciu **Widok > składanie > Fold przełącznika / Przełącz wszystkie złożeń** element menu:

 ![Składanie elementu Menu](media/source-editor-image19.png)

Ten element menu można również włączyć lub wyłączyć składania kodu.

## <a name="white-space"></a>Biały znak

Może być konieczne do wyświetlenia niewidoczne znaki w kodzie źródłowym. Jest widoczny sposób, aby upewnić się, że w przypadku przestrzega standardy kodowania i nie niepotrzebnie marnować miejsca. Jest również przydatne w przypadku zapisywania F #, który jest zależny od dokładnie wcięta wierszy do obliczania kodu.

Ustaw opcje mają odstępu, przechodząc do **programu Visual Studio > Preferencje > Edytor tekstu > Znaczniki i linijki**. Ta opcja umożliwia ustawienie _podczas_ znaki widoczne będą wyświetlane: nigdy w zaznaczeniu lub zawsze:

 ![Pokaż opcje niewidoczne znaków](media/source-editor-image3.png)

Opcję, aby wyświetlić karty, spacje i zakończenia wierszy jest również dostępna:

 ![Pokaż karty i spacji](media/source-editor-image4.png)

 Niewidoczne znaki są wyświetlane jako szare kropkami, jak pokazano na poniższej ilustracji:

 ![wyświetlane odstępu](media/source-editor-image22.png)


## <a name="ruler"></a>Linijki

Linijki kolumny jest przydatna do określania długości wiersza, szczególnie w przypadku, gdy praca w zespół, który zawiera wytyczne długość wiersza. Linijki kolumny może być włączony lub wyłączony przechodząc do **programu Visual Studio > Preferencje... > Edytor tekstu > Znaczniki i linijki** i zostanie wybrana (lub usunięcie zaznaczenia) **linijki Pokaż kolumnę**, jak pokazano w na poniższej ilustracji:

 ![](media/source-editor-image5.png)

 Zostaną wyświetlone jako pionowy szara linia światła w edytorze źródła.


## <a name="highlight-identifier-references"></a>Wyróżnij odwołania do identyfikatorów

"Wyróżnij odwołania do identyfikatorów" opcja jest włączona można wybrać dowolny symbol w kodzie źródłowym i Edytor źródła zapewni visual przewodnik dotyczący wszystkie odwołania w tym pliku. Aby włączyć tę opcję, przejdź do **programu Visual Studio > Preferencje... > Edytor tekstu > Znaczniki i linijki** i wybierz _Wyróżnij odwołania do identyfikatorów_, jak pokazano na poniższej ilustracji:

![](media/source-editor-image6.png)

Kolor wyróżnienia jest również przydatne w przypadku określające, że coś jest jest przypisany lub odwołuje się do. Jeśli coś jest przypisane, jest wyróżnione kolorem czerwonym; Jeśli jest do niego odwołania, jest zaznaczone na niebiesko:

![](media/source-editor-image7.png)



