---
title: 'Przewodnik: debugowanie arkusza stylów XSLT'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 3db9fa5a-f619-4cb6-86e7-64b364e58e5d
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ebc8e8f8700690a2ae74fcc91384fb77b238ea33
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693399"
---
# <a name="walkthrough-debug-an-xslt-style-sheet"></a>Wskazówki: Debugowanie arkusz stylów XSLT

Kroki opisane w tym przewodniku pokazują, jak używać debuger XSLT. Kroki obejmują wyświetlanie zmiennych, ustawianie punktów przerwania i krokowe wykonywanie kodu. Arkusz stylów znajduje wszystkie źródłowe, których koszt poniżej średnią cenę książek.

## <a name="to-prepare-for-this-walkthrough"></a>Aby przygotować się do tego przewodnika

1.  Zamknij wszystkie otwarte rozwiązania.

2.  Skopiuj dwa przykładowe pliki na komputerze lokalnym.

## <a name="start-debugging"></a>Rozpocznij debugowanie

### <a name="to-start-debugging"></a>Aby rozpocząć debugowanie

1.  Z **pliku** menu wskaż **Otwórz**i kliknij przycisk **pliku**.

2.  Zlokalizuj *belowAvg.xsl* plik i kliknij przycisk **Otwórz**.

     Arkusz stylów jest otwarty w edytorze XML.

3.  Kliknij przycisk Przeglądaj (**...** ) na **dane wejściowe** pola w oknie właściwości dokumentu.

4.  Zlokalizuj *books.xml* plik i kliknij przycisk **Otwórz**.

     Pojedynczy plik dokument źródłowy, który służy do przekształcenia XSLT.

5.  Kliknij prawym przyciskiem myszy `xsl:if` tag początkowy, wskaż pozycję **punktu przerwania**i kliknij przycisk **wstawić punktu przerwania**.

6.  Kliknij przycisk **debugowania XSL** przycisk na pasku narzędzi edytora XML.

To spowoduje uruchomienie procesu debugowania i otwiera kilka nowych systemu windows, które są używane przez debuger.

Istnieją dwa okna wyświetlające wejściowych arkusza stylów i dokumentów. Debuger używa te okna, aby wyświetlić bieżący stan wykonania. Debuger jest ustawiony na `xsl:if` element arkusza stylów i w pierwszym węźle książki w *books.xml* pliku.

**Zmiennych lokalnych** Wyświetla okno zmiennych lokalnych i ich wartości. W tym zmienne zdefiniowane w arkuszu stylów, a także zmienne używane przez debuger do śledzenia węzły, które są obecnie w kontekście.

**Dane wyjściowe XSL** wyświetlany w oknie danych wyjściowych transformacji XSL. To okno jest oddzielony od **programu Visual Studio dane wyjściowe** okna.

## <a name="watch-window"></a>okno czujki

### <a name="to-use-the-watch-window"></a>Aby korzystanie z okna czujki

1.  Z **debugowania** menu wskaż **Windows**, wskaż polecenie **czujki**i kliknij przycisk **1 czujki**.

     Dzięki temu **1 czujki** okno jest widoczne.

2.  Typ `$bookAverage` w **nazwa** pole i naciśnij klawisz **Enter**.

     Wartość `$bookAverage` zmiennej jest wyświetlany w oknie.

3.  Typ `self::node()` w **nazwa** pole i naciśnij klawisz **Enter**.

     `self::node()` to wyrażenie XPath, które ocenia do bieżącego węzła kontekstu. Wartość `self::node()` wyrażenie XPath jest pierwszy węzeł książki. To zmiany możemy przejść przez transformacji.

4.  Rozwiń węzeł `self::node()` węzeł, a następnie rozwiń węzeł `price` węzła.

     Dzięki temu można zobaczyć wartość ceny książki i można łatwo porównać do `$bookAverage` wartości. Ponieważ cena książki jest niższa niż średnia, `xsl:if` warunku ma być pomyślnie wykonane.

## <a name="step-through-the-code"></a>Kroków opisanych w kodzie
 Debuger umożliwia wykonanie jednego wiersza kodu w czasie.

### <a name="to-step-through-the-code"></a>Do wykonania kroków opisanych w kodzie

1.  Naciśnij klawisz **F5** aby kontynuować.

     Ponieważ spełnione pierwszego węzła książki `xsl:if` węzła książki warunek, jest dodawany do **dane wyjściowe XSL** okna. Debuger kontynuuje wykonywanie do momentu znajduje się ponownie na `xsl:if` elementu w arkuszu stylów. Debuger jest teraz ustawiony na drugi węzeł książki w *books.xml* pliku.

     W **1 czujki** okna `self::node()` zmiany wartości na drugi węzeł książki. Sprawdzając wartość elementu cen, można określić, że cena jest powyżej średniej, w związku z tym `xsl:if` warunku powinna zakończyć się niepowodzeniem.

2.  Naciśnij klawisz **F5** aby kontynuować.

     Ponieważ drugiego węzła książki nie spełnia `xsl:if` warunku, węzeł książki nie zostanie dodany do **dane wyjściowe XSL** okna. Debuger kontynuuje wykonywanie do momentu znajduje się ponownie na `xsl:if` elementu w arkuszu stylów. Debuger jest teraz ustawiony na trzeci `book` w węźle *books.xml* pliku.

     W **1 czujki** okna `self::node()` zmiany wartości na trzeci węzła książki. Sprawdzając wartość `price` elementu, można określić, że cena jest poniżej średniej, w związku z tym `xsl:if` warunku ma być pomyślnie wykonane.

3.  Naciśnij klawisz **F5** aby kontynuować.

     Ponieważ `xsl:if` był spełniony warunek, trzeci książki jest dodawany do **dane wyjściowe XSL** okna. Zostaną przetworzone wszystkie źródłowe w dokumencie XML i zatrzymuje się debuger.

## <a name="sample-files"></a>Przykładowe pliki

Następujące dwa pliki są używane przez przewodnika.

### <a name="belowavgxsl"></a>belowAvg.xsl

```xml
<?xml version='1.0'?>
<xsl:stylesheet version="1.0"
      xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" encoding="utf-8"/>
  <xsl:template match="/">
    <xsl:variable name="bookCount" select="count(/bookstore/book)"/>
    <xsl:variable name="bookTotal" select="sum(/bookstore/book/price)"/>
    <xsl:variable name="bookAverage" select="$bookTotal div $bookCount"/>
    <books>
      <!--Books That Cost Below Average-->
      <xsl:for-each select="/bookstore/book">
        <xsl:if test="price < $bookAverage">
          <xsl:copy-of select="."/>
        </xsl:if>
      </xsl:for-each>
    </books>
  </xsl:template>
</xsl:stylesheet>
```

### <a name="booksxml"></a>Books.XML

```xml
<?xml version='1.0'?>
<!-- This file represents a fragment of a book store inventory database -->
<bookstore>
  <book genre="autobiography" publicationdate="1981" ISBN="1-861003-11-0">
    <title>The Autobiography of Benjamin Franklin</title>
    <author>
      <first-name>Benjamin</first-name>
      <last-name>Franklin</last-name>
    </author>
    <price>8.99</price>
  </book>
  <book genre="novel" publicationdate="1967" ISBN="0-201-63361-2">
    <title>The Confidence Man</title>
    <author>
      <first-name>Herman</first-name>
      <last-name>Melville</last-name>
    </author>
    <price>11.99</price>
  </book>
  <book genre="philosophy" publicationdate="1991" ISBN="1-861001-57-6">
    <title>The Gorgias</title>
    <author>
      <name>Plato</name>
    </author>
    <price>9.99</price>
  </book>
</bookstore>
```

## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu XSLT](../xml-tools/debugging-xslt.md)