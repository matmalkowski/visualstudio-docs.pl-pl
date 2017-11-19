---
title: Refaktoryzacji kodu w programie Visual Studio for Mac | Dokumentacja firmy Microsoft
description: "Ponowne porządkowanie kodu w programie Visual Studio dla komputerów Mac jest łatwiejsza obsługa przy użyciu analizy źródła."
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: C7782BF3-016F-4B41-8A81-85FC540A1A8F
ms.openlocfilehash: ba92cd9a0e9ca28d132116f65fd41758bce1a1f0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="refactoring"></a>Refaktoryzacja

Refaktoryzacji kodu jest sposób rozmieszczanie, restrukturyzacji i wyjaśnienia jednoczesnym zapewnieniu ogólnej zachowania kodu nie powoduje zmiany istniejącego kodu.

Tworzy zdrowsze baza kodu, co znacznie bardziej użyteczny, do odczytu i łatwy w obsłudze można lub inne dewelopera lub użytkownika, który może odwoływać się do kodu.

Program Visual Studio dla komputerów Mac dla integracji z Roslyn, platformy .NET kompilatora typu open source firmy Microsoft, umożliwia więcej refaktoryzacji operacji, a także pełni obsługi najnowszej wersji języka C#.

## <a name="renaming"></a>Zmiana nazwy 

*Zmienić* refaktoryzacji polecenie pozwala na dowolnym identyfikator kodu (na przykład nazwa klasy, nazwy właściwości itp.) Znajdź wszystkie wystąpienia tego identyfikatora i należy je zmienić. Aby zmienić nazwę symbolu, kliknij prawym przyciskiem myszy na nim i wybierz polecenie **Refaktoryzuj > Zmień nazwę**, lub **Cmd + R** klucza powiązania:

![Zmień nazwę elementu menu](media/refactoring-renaming1.png)

Spowoduje to zaznacz symbolu i wszelkie odwołania do niego. Po ponownym uruchomieniu, wpisując nazwę nowej automatycznie zmieni wszystkie odwołania w kodzie i sygnalizuje Twojej zakończenia zmiany nazwy, naciskając **Enter**:

 ![Zmiana nazwy i identyfikatora](media/refactoring-renaming2.png)

## <a name="context-actions"></a>Kontekst akcji

Kontekst akcji pozwalają sprawdzić żadnego kodu C# i Zobacz wszystkie możliwe opcje refaktoryzacji. 

**Rozwiązać** i **Refaktoryzuj** kontekstu elementy są łączone w pojedynczy *Quick Fix...*  elementu, który zapewnia wszystkie dostępne akcje kontekstowe:

![Wyświetl elementy kontekstu](media/refactoring-context-action.png)

Ustawiając kursor nad wszystkie akcje kontekstowe pozwoli Podgląd co zostaną dodane lub usunięte w kodzie.

Alternatywnie możesz nacisnąć przycisk **opcji + Enter** dowolne miejsce w kodzie:

![Opcja kontekstu wprowadź elementów](media/refactoring-image2a.png)

Aby włączyć te opcje, należy wybrać *Włącz analizę źródła otwartych plików* w opcjach **programu Visual Studio for Mac > Preferencje > Edytor tekstu > analizy źródła**:

 ![Włączenie analizy źródła](media/refactoring-options.png)

Istnieje ponad 100 możliwych akcji, które mogą być sugerowane, które są włączone lub wyłączone, przechodząc do **programu Visual Studio for Mac > Preferencje > analizy źródło > C# > Akcje kodu** i zaznaczając lub unselecting pole obok pozycji Akcja:

 ![Akcje analizy źródłowego C#](media/refactoring-image3a.png)

### <a name="common-context-actions"></a>Typowe akcje kontekstu

Poniżej opisano niektóre akcje kontekstu przede wszystkim często używane.

#### <a name="extract-method"></a>Wyodrębnij — metoda

Operacja refaktoryzacji wyodrębniania metody umożliwia utworzenie nowej metody wyodrębniając wybór kodu w istniejącego elementu członkowskiego. Ta akcja spowoduje wykonać dwie czynności:

* Tworzy nową metodę wybranego kodem
* Wywołuje nowej metody, w tym miejscu, gdzie został zaznaczony kod.

##### <a name="example"></a>Przykład

1. Dodaj następujący kod:

```
    class MainClass
    {

        double CalculatePyramidVolume(double baseArea, double height)
        {

            double volume = (baseArea * height) / 3;

            return volume;
        }
    }
```

2. Zaznacz wiersz `double volume = (baseArea * height) / 3;`, kliknij prawym przyciskiem myszy kliknij go, a wybierz **Refaktoryzuj > Wyodrębnij metodę**.

3. Użyj klawiszy strzałek, aby wybrać, gdzie nowa metoda ma zostać umieszczony w kodzie.


#### <a name="encapsulate-field"></a>Hermetyzuj pole

Operacja Hermetyzuj pole służy do tworzenia właściwości z istniejącym polem i aktualizuje swój kod, aby nowo utworzony właściwości odwołania. Tworząc właściwość, która hermetyzuje pola, możesz są brak zezwolenia bezpośredni dostęp do pola publicznego, co oznacza, że inne obiekty nie można go modyfikować.

Ta akcja spowoduje wykonanie następujących czynności:

* Zmiany modyfikator dostępu prywatnego.
* Generuje określonej metody pobierającej i ustawiającej dla pola (chyba że pole jest tylko do odczytu, w którym to przypadku tylko utworzy on metodę pobierającą).


## <a name="source-analysis"></a>Analiza źródła

Analiza źródła będzie analizować kodu na bieżąco potencjalne błędy podkreślenia i naruszeń styl, i zapewniając automatyczne poprawki jako kontekst akcji. 

Aby wyświetlić wszystkie wyniki analizy źródła dla dowolnego pliku w dowolnym momencie, wyświetlanie paska przewijania w prawej części edytora tekstu:

 ![Pasek boczny analizy źródła](media/refactoring-image4a.png)

Kliknięcie okręgu u góry, można wykonać iterację każdego sugestię o najwyższej ważności przedstawiający pierwszy. Ustawiając kursor nad wynik lub wiersza spowoduje wyświetlenie problem można naprawić za pomocą kontekstu akcji:

 ![Element źródłowy analizy](media/refactoring-image5.png)

