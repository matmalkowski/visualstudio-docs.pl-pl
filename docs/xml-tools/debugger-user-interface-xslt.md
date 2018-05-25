---
title: Interfejs użytkownika debuger (XSLT)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: reference
ms.assetid: 846fdabd-e5c3-4688-9b0d-a93fbeea1b96
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6f3d9dafc2911e05fd76aadd5b08ad2327969839
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2018
---
# <a name="debugger-user-interface-xslt"></a>Interfejs użytkownika debuger (XSLT)

W tym temacie opisano debugera systemu windows i oknach dialogowych. Zostało omówione tylko elementów interfejsu użytkownika, które zachowują się specyficzne dla XSLT debugowania.

Aby uzyskać więcej informacji, zobacz [debugowania odwołanie do interfejsu użytkownika](../debugger/debugging-user-interface-reference.md).

## <a name="locals-window"></a>okno zmiennych lokalnych
 Okno zmiennych lokalnych Wyświetla informacje zdefiniowane w arkuszu stylów. Okno zmiennych lokalnych zawiera trzy kolumny informacji:

 **Nazwa**

 Ta kolumna zawiera nazwy wszystkich zmiennych lokalnych w bieżącym zakresie. Ustawia węzeł ma formantem drzewa, które użytkownik może przejść do jego podfolderach w temacie.

 **Wartość**

 Ta kolumna zawiera wartości zawarty w każdej zmiennej. Atrybut przetwarzania instrukcji, komentarza, tekst i węzły CData wyświetlona wartość tekstu węzła. Węzły Namespace wyświetlić identyfikator URI przestrzeni nazw.

 **Typ**

 Ta kolumna określa typ danych na liście zmiennych **nazwa** kolumny.

 Okno zmiennych lokalnych są również wyświetlane zmiennych kontekstu wstępnie zdefiniowanych, które śledzą kontekście transformację XSLT. W poniższej tabeli opisano zmiennych kontekstu wstępnie zdefiniowanych przez debuger XSLT.

|Nazwa|Opis|
|----------|-----------------|
|`last()`|Rozmiar kontekstu.|
|`position()`|Pozycja lub numer indeksu węzła kontekstu względem rozmiaru kontekstu.|
|`self::node()`|Wartość węzła kontekstu.|

## <a name="output-window"></a>Okno wyniku
 W oknie danych wyjściowych zawiera wszystkie komunikaty o błędach lub wyjątki zabezpieczeń, jakie występują podczas debugowania.

 Debuger XSLT używa osobnym oknie do wyświetlania danych wyjściowych debugera. To jest tym samym oknie używany do wyświetlania danych wyjściowych z **Pokaż dane wyjściowe XSL** polecenia.

## <a name="task-list"></a>Lista zadań
 **Listy zadań** zawiera listę wszystkich błędów kompilacji, w arkuszu stylów. Dwukrotne kliknięcie błąd ma kursor do wiersza z powodu błędu.

 **Listy zadań** obejmuje wszystkie błędy w blokach skryptu w pliku XSLT.

> [!NOTE]
> Debuger XSLT nie zawiera ostrzeżeń, aby nie były wyświetlane w **listy zadań**.

## <a name="breakpoints-window"></a>Okno punktów przerwania
 Okna punktów przerwań przedstawia wszystkich punktów przerwania ustawionych w bieżącym projekcie. Jeśli punkt przerwania zostanie dodany, gdy okno jest widoczne, okno zostanie automatycznie zaktualizowany do Pokaż nowego punktu przerwania.

 Okna punktów przerwań zachowania w przypadku taki sam sposób jak inne debugera programu Visual Studio.

## <a name="command-windowimmediate-window"></a>Okno polecenia/bezpośrednim
 Nie jest zaimplementowana w tej wersji debuger XSLT.

## <a name="watch-window"></a>okno czujki
 Okno czujki jest używany do oceny zmiennych. Można również zmienić wartości zmiennych.

 Okno czujki zmienne są dla bieżącego kontekstu (najwyższy element na stosie wywołań). Jeśli zmienisz kontekście okna czujki aktualizacji i wyświetla zmienne ustawione dla tego kontekstu.

## <a name="call-stack-window"></a>Stos wywołań, okno
 **Stos wywołań** okno służy do wyświetlania nazwy funkcji w stosie wywołań, typy parametrów i wartości parametrów. Informacje stosu wywołań jest wyświetlany tylko wtedy, gdy program debugowany jest w stanie przerwania.

 Stos wywołań reprezentuje różnych kontekstach, które przechodzi przez wykonanie XSLT. Na przykład, jeśli istnieje połączenie z szablonu "a" do szablonu "b", szablon "" i szablon "b", są wyświetlane w **stos wywołań** okna z bieżącego kontekstu na górze listy. Użytkownik jest w stanie wyświetlić kwerendę, która jest aktualnie wykonywany.

 Jeśli szablony nie mają nazwę w pliku XSLT, są używane nazwy generowane przez procesor XSLT.

 Kliknięcie elementu innego niż ten, w górnej części listy wskazuje podglądu, gdzie gałęzi wykonywania XSLT się to zdarzyć przy użyciu standardowych wyróżnianie zielony i zielone strzałki.

## <a name="quickwatch-dialog-box"></a>QuickWatch — okno dialogowe
 **QuickWatch** okno dialogowe jest używany do oceny wyrażenia XPath 1.0. Węzeł kontekstu ( `self::node()` węzeł w oknie zmienne lokalne) udostępnia Kontekst wykonywania wyrażenia XPath. Wynik wykonania wyrażenie XPath jest wyświetlany w oknie wyrażeń kontrolnych.

 Poniższa lista zawiera pewne ograniczenia na Obliczanie wyrażenia XPath.

-   Dozwolone są tylko funkcje wbudowane XPath.

-   XSLT wbudowane funkcje takie jak `document()`, `key()`i tak dalej są niedozwolone.

-   Funkcje zdefiniowane przez użytkownika nie są dozwolone.

Aby uzyskać więcej informacji, zobacz [porady: oceny wyrażenia XPath](../xml-tools/how-to-evaluate-an-xpath-expression.md).

## <a name="disassembly-window"></a>Dezasemblacja, okno
 Dezasemblacja, okno zawiera kod zestawu, który jest generowany przez kompilator XSLT. To okno może służyć w taki sam sposób jak wszystkie inne okna dezasemblacji Visual Studio.

 Aby uzyskać więcej informacji [porady: Korzystanie z okna dezasemblacji](../debugger/how-to-use-the-disassembly-window.md).

## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)
- [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)
- [Sprawdź zmienne w oknach zmiennych automatycznych i zmiennych lokalnych w programie Visual Studio](../debugger/autos-and-locals-windows.md)