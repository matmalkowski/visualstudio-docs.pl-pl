---
title: 'Wskazówki: Korzystanie z hierarchii XSLT | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: a4259a06d79588983e3591510c40e119bc4fcb3b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="walkthrough-using-xslt-hierarchy"></a>Wskazówki: Korzystanie z hierarchii XSLT

Narzędzie hierarchii XSLT upraszcza wiele zadań związanych z projektowaniem XML. Arkusz stylów XSLT często używa `includes` i `imports` instrukcje. Kompilacja rozpoczyna się od arkusza stylów podmiotu zabezpieczeń, ale po wyświetleniu błędu w wyniku kompilowanie arkusz stylów XSLT błędu mogą pochodzić z innego źródła niż arkusza stylów podmiotu zabezpieczeń. Naprawienie błędu lub edycji arkusza stylów mogą wymagać dostępu do arkuszy stylów dołączone lub importowany. Krokowe arkusza stylów w debugerze może Otwórz arkusze stylów dołączone i importowane, i chcesz dodać punkt przerwania w pewnym momencie jednego lub więcej arkuszy stylów dołączone.

Inny scenariusz, gdzie mogą być przydatne narzędzie hierarchii XSLT jest umieścić punkty przerwania reguł wbudowanych szablonów. Szablon reguły są specjalne szablony wygenerowany dla każdego trybu arkusza stylów i wywoływane przez `xsl:apply-templates` po nie innych szablonów nie odpowiada węzła. Aby zaimplementować debugowania w regułach wbudowanych szablonów, debuger XSLT generuje plik z zasadami w folderze tymczasowym i kompiluje je razem z arkusza stylów podmiotu zabezpieczeń. Bez Przechodzenie do kodu z niektórych `xsl:apply-template`, może być trudne można znaleźć arkusze stylów, które zostały uwzględnione w arkuszu stylów główną lub znajdowanie i Otwieranie arkusza stylów przy użyciu reguł wbudowanych szablonów.

W przykładzie, w tym temacie pokazano, debugowania w arkuszu stylów do którego istnieje odwołanie.

## <a name="to-debug-in-a-referenced-style-sheet"></a>Debugowanie w arkuszu stylów do którego istnieje odwołanie

1. Otwórz dokument XML w Visual Studio. W tym przykładzie użyto następujących `collection.xml` dokumentu.  
  
    ```xml
    <?xml version="1.0" encoding="utf-8"?>  
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>  
    <COLLECTION>  
      <BOOK>  
        <TITLE>Lover Birds</TITLE>  
        <AUTHOR>Cynthia Randall</AUTHOR>  
        <PUBLISHER>Lucerne Publishing</PUBLISHER>  
      </BOOK>  
      <BOOK>  
        <TITLE>The Sundered Grail</TITLE>  
        <AUTHOR>Eva Corets</AUTHOR>  
        <PUBLISHER>Lucerne Publishing</PUBLISHER>  
      </BOOK>  
      <BOOK>  
        <TITLE>Splish Splash</TITLE>  
        <AUTHOR>Paula Thurman</AUTHOR>  
        <PUBLISHER>Scootney</PUBLISHER>  
      </BOOK>  
    </COLLECTION>  
    ```

1. Dodaj następujące `xslincludefile.xsl`:

    ```xml
    <?xml version='1.0'?>  
    <xsl:stylesheet version="1.0"  
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"  
          xml:space="preserve">  
  
    <xsl:template match="TITLE">  
       Title - <xsl:value-of select="."/><BR/>  
    </xsl:template>  
  
    <xsl:template match="AUTHOR">  
       Author - <xsl:value-of select="."/><BR/>  
    </xsl:template>  
  
    <xsl:template match="PUBLISHER">  
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->  
    </xsl:template>  
  
    </xsl:stylesheet>  
    ```
  
3.  Dodaj następujące `xslinclude.xsl` pliku:  
  
    ```xml
    <?xml version='1.0'?>  
    <xsl:stylesheet version="1.0"  
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">  
  
      <xsl:output method="xml" omit-xml-declaration="yes"/>  
  
      <xsl:template match="/">  
        <xsl:for-each select="COLLECTION/BOOK">  
          <xsl:apply-templates select="TITLE"/>  
          <xsl:apply-templates select="AUTHOR"/>  
          <xsl:apply-templates select="PUBLISHER"/>  
          <BR/>  
          <!-- add this -->  
        </xsl:for-each>  
      </xsl:template>  
  
      <!-- The following template rule will not be called,  
      because the related template in the including stylesheet  
      is called. If we move this template so that  
      it follows the xsl:include instruction, this one  
      will be called instead.-->  
      <xsl:template match="TITLE">  
        <DIV STYLE="color:blue">  
          Title: <xsl:value-of select="."/>  
        </DIV>  
      </xsl:template>  
  
      <xsl:include href="xslincludefile.xsl" />  
    </xsl:stylesheet>  
    ```
  
4.  Dodaj punkt przerwania w instrukcji `<xsl:include href="xslincludefile.xsl" />`.
  
5.  Rozpocznij debugowanie.  
  
6.  Gdy debuger zatrzymuje się na instrukcję `<xsl:include href="xslincludefile.xsl" />`, naciśnij klawisz **Step Into** przycisku. Należy pamiętać, że debugowanie może być kontynuowane w arkuszu stylów do którego istnieje odwołanie. Hierarchia jest widoczna i Projektant zawiera prawidłową ścieżkę.  
  
## <a name="see-also"></a>Zobacz także

[Przewodnik: Profiler XSLT](../xml-tools/walkthrough-xslt-profiler.md)