---
title: "Edytor źródła | Dokumentacja firmy Microsoft"
description: "Za pomocą edytora źródła w programie Visual Studio dla komputerów Mac"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: f52e60c0ade8cebc78b3408b4ef81ef85fcd767b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="source-editor"></a>Edytor źródła

Edytor wiarygodnego źródła jest konieczne do pisania kodu krótkiej formie i wydajne. Programu Visual Studio for Mac zawiera Edytor zaawansowane źródła, który znajduje się na środku interakcji z IDE. Edytor źródła zawiera funkcje, które mogą oczekiwać, należy wykonać swoją pracę z łatwością: od podstaw takie wyróżnianie składni, fragmentów kodu i składania kodu, do korzystania z integracji kompilatora Roslyn, takie jak IntelliSense funkcjonalnej kodu ukończenia.

Edytor źródła w programie Visual Studio for Mac umożliwia bezproblemowe z wszystkie inne funkcje udostępniane przez IDE, takie jak debugowania, refaktoryzacji elementu i integracją kontroli wersji.

W tym temacie przedstawiono niektóre główne funkcje Edytor źródła i opisuje, jak można programu Visual Studio for Mac produktywność jak to możliwe.

## <a name="the-source-editor-experience"></a>Środowisko Edytor źródła

Wyświetlanie i przenoszenie wydajnie w całym kodzie jest integralną częścią przepływu pracy programowania. Dokładnie, jak użytkownik chce wyświetlać i obsługa, że kod jest osobiste decyzji, który różni się między deweloperzy - i często między projektami.

Program Visual Studio dla komputerów Mac oferuje wiele zaawansowanych funkcji, aby wiele platform jako dostępny i użyteczna, jak to możliwe. W poniższych rozdziałach opisano niektóre najważniejsze funkcje.


### <a name="code-folding"></a>Składanie kodu

Kod składania ułatwia zarządzanie plików kodu źródłowego dużych przez deweloperów pokazać lub ukryć pełną części kodu, na przykład przy użyciu dyrektyw, schematyczny kod i komentarze i instrukcje #region. To jest domyślnie wyłączona w programie Visual Studio dla komputerów Mac

Aby włączyć składania kodu, przejdź do **programu Visual Studio > Preferencje... > Edytor tekstu > Ogólne > Kod składania**:

![Kod składania opcje](media/source-editor-image1.png)

Oprócz opcję, aby włączyć kod składania tego menu zawiera także opcję fold #regions i komentarze domyślnie wyświetlania o nazwie wskazówki, zamiast kodu.

Aby pokazać lub ukryć sekcje, należy użyć widget ujawniania obok numer wiersza:

 ![Pokazywanie lub ukrywanie sekcje w kodzie](media/source-editor-image2.png)

Można również przełączać się między pokazywanie i ukrywanie złożeń przy użyciu **Widok > składanie > Fold przełącznika / Przełącz wszystkie złożeń** element menu:

 ![Składanie elementu Menu](media/source-editor-image19.png)

Ten element menu można również włączyć lub wyłączyć składania kodu.

### <a name="white-space"></a>Biały znak

Może być konieczne, można mieć możliwość wyświetlania niewidoczne znaki w kodzie źródłowym. Jest widoczny sposób, aby upewnić się, że są spełnione standardy kodowania i nie niepotrzebnie marnować miejsca. Istnieje również przydatne podczas zapisywania F #, który jest zależny od dokładnie wcięta wierszy do obliczania kodu.

Ustaw opcje mają odstępu, przechodząc do **programu Visual Studio > Preferencje > Edytor tekstu > Znaczniki i linijki**, jak pokazano poniżej. Ta opcja umożliwia ustawienie _podczas_ znaki widoczne będą wyświetlane: nigdy w zaznaczeniu lub zawsze:

 ![Pokaż opcje niewidoczne znaków](media/source-editor-image3.png)

Opcję, aby wyświetlić karty, spacje i zakończenia wierszy jest również dostępna:

 ![Pokaż karty i spacji](media/source-editor-image4.png)

 Niewidoczne znaki są wyświetlane jako punktów szare, jak przedstawiono poniżej:

 ![wyświetlane odstępu](media/source-editor-image22.png)


### <a name="ruler"></a>Linijki

Wyświetlanie linijki kolumny jest przydatne w przypadku określania długości wiersza, szczególnie w przypadku, gdy praca w zespół, który zawiera wytyczne długość wiersza. Linijki kolumny może być włączony lub wyłączony przechodząc do **programu Visual Studio > Preferencje... > Edytor tekstu > Znaczniki i linijki** i zostanie wybrana (lub usunięcie zaznaczenia) **linijki Pokaż kolumnę**, jak pokazano poniżej:

 ![](media/source-editor-image5.png)

 Zostaną wyświetlone jako światła szare linią pionową w edytorze źródła.


### <a name="highlight-identifier-references"></a>Wyróżnij odwołania do identyfikatorów

Gdy ta opcja jest włączona, deweloper można umieścić wskaźnik myszy na dowolny symbol w kodzie źródłowym i Edytor źródła zapewnia visual przewodnik dotyczący wszystkie odwołania w tym pliku. Jest włączona przechodząc do **programu Visual Studio > Preferencje... > Edytor tekstu > Znaczniki i linijki** i wybierając _Wyróżnij odwołania do identyfikatorów_, jak pokazano poniżej:

![](media/source-editor-image6.png)

Kolor wyróżnienia jest również przydatne w przypadku określające, że coś jest jest przypisany lub odwołuje się do. Jeśli coś jest przypisane, jest wyróżnione kolorem czerwonym; Jeśli jest do niego odwołania, jest zaznaczone na niebiesko:

![](media/source-editor-image7.png)



